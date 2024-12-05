# Volumes
## EBS Volume
* If servers are physical we can copy the data to a pendrive, Floppy or CD and External Hard Disk and share data with other server. We can store the data in Google drive and give access to the data.
* In Virtual machine all this is not possible .
* Our instances come with a default volume, this default volume is root volume. We can't remove root volume. But we can add additional volume which is called as `EBS Volume(Elastic Block Storage)`
* `EBS volumes` are specific to `Availability Zone(AZ)` and can only be attached to instances within the same AZ.
  
### Features of EBS
1. Scalability
2. Backup
3. Encription
4. Charges: AWS charges EBS as per the volume size created. EBS charges vary from region to region.
5. Independent: EBS are independent on EC2 instances.

### Types of EBS
1. **SSD:** Suitable for small chunks of data that requires fast I/Ops. Can be used as root volumes for EC2 instances.
2. **General Purpose SSD(GP2):** Speed is 3-10000 IOps.
3. **Provisioned IOps SSD(IO1):** Max speed is 20000IOps
* **`IOps`** is capacity that persecond your storage can read.
* There are other types too but we are no longer using them for production.
  
## Creating EBS and Mounting to the EC2
* Create an EC2 instance (Create in a AZ )(Name = EBS-SERVER-1) 
* While creating instance in configure storage --> add volume --> select type of volume.
* Select the subnet in which AZ you want to create.

  ![preview](images/AWS49.png)

* In configure storage session.
  
  ![preview](images/AWS50.png)
  ![preview](images/AWS51.png)

* After creation on ec2 check two volume are there or not.
  
  ![preview](images/AWS52.png)

* Now login into EC2 and configure additional storage we added while launching the instance.
* After login run these commands.

```bash
df -h # to see storages
lsblk # List block: this cmd will display additional storage that your instance have.
```

![preview](images/AWS53.png)

* When we connect a pendrive to your laptop(physical server) we can see a folder for pendrive. But for virtual machine when an additional storage is attached to the instance we can't see the folder for that(not auto mounted to the server).
* So to mount the stirage to the server, First we have to formate, Create folder and mount the storage to that folder.

1. **Formate:**
```bash
sudo mkfs -t ext4 /dev/xvdb
# mkfs is make filesystem
```
* This command  will formate the storage, We have to formate because we are connecting to the storage for the 1st time.
  
2. **Create a folder and mount:** To mount the storage we have to create a folder.
```bash
sudo mkdir /app-data
sudo mount /dev/xvdb /app-data/
df -h # check whether it is mounted or not
```

![preview](images/AWS54.png)

* I changed the name of the host for better understanding.
```bash
sudo vi /etc/hostname # change name and save the file
sudo init 6 # restart the system and login into the server again.
```

![preview](images/AWS55.png)

* Now whatever I store in `/app-data` will directly stored in `/dev/xvdb`
* Now try to do some changes in the `/app-data`.

![preview](images/AWS56.png)
![prevew](images/AWS57.png)

* It is throwing permssion denied when I am trying to create a file because `/app-data` owner is `root`
* Change the ownership of the `/app-data` 
```bash
sudo chown ec2-user:ec2-user /app-data
```
![preview](images/AWS58.png)

* Now try to create a file and add content to it.
  
  ![preview](images/AWS59.png)

### How to transfer data to other instance in same Availability zone?
* Create a EC2(Name = EBS-SERVER-1a)un same AZ of above EC2.
  
  ![preview](images/AWS63.png)

* In `EBS-SERVER-1`, we have to unmount the storage 
```bash
sudo umount /dev/xvdb
df -h
```
![preview](images/AWS60.png)


* Now detach the volume. volumes --> select volume --> Actions --> Detach volume.
  
  ![preview](images/AWS61.png)
  ![preview](images/AWS62.png)

* Attach the detached volume to `EBS-SERVER-1a`. select volume --> Select the AZ --> Select the EC2.
  
  ![preview](images/AWS65.png)
  ![preview](images/AWS66.png)

* After attaching the EBS we have to mount the storage. No need to do formate. Check whether the data is there or not. 
  
  ![preview](images/AWS68.png)
  ![preview](images/AWS67.png)

### How to connect EBS volume of one AZ to EC2 instance of other AZ?
* We should transfer the volume to a different AZ to do so we have to create `Snapshot` out of `EBs Volume`.
* We can also cpoy snapshot from one region to other region.


**AWS EBS Snapshot:** EBS snapshots are point-in time images or copies of your EBS volumes. While EBS volumes are AZ specifics but Snapshots are Region-specofic. Max of 500- images/copies volumes per account and upto 10000 EBS snapshots can be crated.

#### Steps to connect EBS with instance in other AZ
1. Create Snapshot from the volume. Select volume --> actions --> create snapshot.
   
   ![preview](images/AWS69.png)
   ![preview](images/AWS70.png)

2. Once the snapshot is ready, We can create a new volume form that snapshot in desired AZ.

Snapshot --> actions  --> create volume --> select size --> select AZ --> Create volume.

![preview](images/AWS71.png)
 
![preview](images/AWS72.png)

* Select In which availabilty zone you want to create EBS volume.

3. Now we can attach EC2 to the new volume. We have to mount the volume and check wheather the data is present or not.
  * I have created an EC2 instance in us-east-1b.
  
  ![preview](images/AWS73.png)
  ![preview](images/AWS74.png)
  ![preview](images/AWS75.png)
  ![preview](images/AWS76.png)

### Data Lifecycle Manager(DLM):
* Automate the creation, retention, copy and deletion of `snapshots` and `AMIs`.
  
#### Create DLM
1. In EC2 --> Elastic block store --> Lifecycle manager
![preview](images/AWS77.png)
![preview](images/AWS78.png)
![preview](images/AWS79.png)
![preview](images/AWS80.png)
![preview](images/AWS81.png)
![preview](images/AWS82.png)
