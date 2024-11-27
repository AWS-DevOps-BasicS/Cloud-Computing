# VPC Peering Connection
* Imagine there are 2 VPC(DELL-VPC & ACC-VPC) both of them working for same client(Uber). Acc is managing customer details of client and DELL is managing customer details of client.
* In ACC-VPC, maintains a Database which contains customer details in Pvt-Subnet.
* In DELL-VPC, maintains a Database which contains payment details in Pvt-Subnet.
* If DELL needs to access to customer details and ACC needs payment details. They have to exchange information from one pvt server of one VPC to another pvt server of other VPC.
* To communicate with the Private server in one VPC we need a bastion host or jump server.
* **Bastion host** present in same network exposed to public network from there we can connect with pvt servers.

### Lab Setup
* Create 2 VPC.
  
  ![preview](images/peering1.png)
  ![preview](images/peering2.png)

* Now I will be launching 2 EC2 instances in those Pvt-Subnet that I have created earlier.

![preview](images/peering3.png)
![preview](images/peering4.png)

* In order to connect with pvt ec2s we need a bastion host in respective networks.
* For Bastion host, we have to launch ec2 instances in pub-subnets.
  
![preview](images/peering5.png)
![preview](images/peering6.png)

* From Public server to connect with private server we need pem file of private server to be be present in public server.
* Pem file is present in local server we have to send the pem file from local server to public server.
```bash
 #scp -i .\<pem file name> .\<file you want to transfer> <username>@<ip address>:~
 scp -i .\acc.pem .\acc.pem ec2-user@54.175.152.52:~ # for acc, :~ is to copy the file to home directory
 scp -i .\dell.pem .\dell.pem ec2-user@13.234.76.202:~
 ```
 
 ![preview](images/peering7.png)
 ![preview](images/peering8.png)

* pem file should not have read and write permission so I have changed the permission of pem file.
```bash
chmod 400 acc.pem
chmod 400 dell.pem
```
 
 ![preview](images/peering9.png)
 ![preview](images/peering10.png)

* In ACC-VPC, pvt-server have a file that file has to transfered to Dell-Pvt server.
  
  ![preview](images/peering11.png)

* For this transfer the pemfile of DELL-pvt server to ACC-pvt server and then try to send the file you want to share.
  
  ![preview](images/peering12.png)

* This is where `VPC peering` comes into picture.
  
 **_VPC Peering connection is a networking connection between 2 VPC that enables you to route the traffic between them. Instances in 2 VPCs can communicate with each other as if they are within the same network._**
  
* VPC peering is a 2 way connection, Peering is like friend request, once we send the VPC peering request then other VPC have to accept the request. These VPC CIDR should not collide with each other.

### Create a VPC peering
  
  ![preview](images/peering13.png)
  ![preview](images/peering14.png)
  ![preview](images/peering15.png)
  ![preview](images/peering16.png)
  ![preview](images/peering17.png)

* Now try to send the file to dell-pvt server fro acc-pvt.
  
  ![preview](images/peering18.png)

* Connection is not established because, After peering connection is done to send & receivce traffic across VPC peering connection, you must add a route to the peered VPC in route table.
  
  * In ACC-Pvt-RT,
  
  ![preview](images/peering19.png)

  * In DELL-Pvt-RT,
  
  ![preview](images/peering20.png)

* Now try to send the file.
  
  ![preview](images/peering21.png)
  ![preview](images/peering22.png)

* We can log into the dell-pvt server from acc-pvt server.
  
  ![preview](images/peering23.png)

* We can do the same process from dell servers to.