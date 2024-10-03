# Networking
* Inside the public cloud we can create a private cloud which is virtual.
* AWS provides `VPC(Virtual Private Cloud)` service to create a private cloud virtually.
* Dividing the network is called `Subnetwork` and the process is called `Subnetting`.
* To provide security for the network AWS have `NACL(Network Access Control List)`. `NACL` has a list of IP addresses  which should be allowed and denied.
* In virtual environment, If somebody want to reach you then you need internet access so AWS provides `IGW(Internet Gateway)` which provide internet access to nework(VPC).
* Traffic distribution between different subnets happends using `Route Tables`.
* We have to set a CIDR for the ip addresses and to create a VPC we need CIDR.
* To create a VPC IPV4 CIDR is using.
* **CIDR(Classless Inter Domain Routing):**
  * We have two types: 
      1. IPV4: it has 4 octets. each octet contains 8 bits. It is a 32 bit address.
      2. IPV6: 128 bits -->hexadecimal --> x:x:x:x:x:x:x:x
* Each octet have 8 bits that represents values from 0 to 255.
* To design the network cidr you use [cidr xyz](https://cidr.xyz/) calculator.
* Our client requirement is to have ip addresses for 8000. So CIDR is 10.0.0.0/19 where 32-19 = 13 --> 2<sup>13</sup>=8192.
* **Network CIDR:**
  
  ![preview](images/AWS37.png)

* But in future we may increase the number of server in the VPC then we can't modify the VPC cidr. So we will create with max subnet mask provided by AWS is `/16`.
* Each subnet should have capacity of 4k servers. 
  
* **Sunbet-1:** 
  
  ![preview](images/AWS38.png)

* **Subnet-2:**

  ![preview](images/AWS39.png)

### Creation on VPC in AWS:
* In AWS console, go to search and search for `VPC`.
* Create  VPC --> Enter name of VPC --> Enter cidr range.
  
  ![preview](images/AWS2.png)
  ![preview](images/AWS3.png)
  ![preview](images/AWS4.png)

* Now we have create two subnets.
  
  ![preview](images/AWS5.png)
  ![preview](images/AWS6.png)
  ![preview](images/AWS7.png)
  ![preview](images/AWS8.png)
  ![preview](images/AWS9.png)

*  Now create two route tables one for app subnet and one for db subnet.
  
  ![preview](images/AWS10.png)

*  Create Route table for DB subnet similarlly create for APP subnet too. 
  
  ![preview](images/AWS12.png)

* After create of route tables in subnet association add the respective subnets.
  
  ![preview](images/AWS11.png)
  ![preview](images/AWS13.png)

* For internet access to the network we created earlier we have to create IGW.
  
  ![preview](images/AWS14.png)
  ![preview](images/AWS15.png)

* Attach the VPC to the IGW.
  
  ![preview](images/AWS16.png)
  ![preview](images/AWS17.png)

* To give internet access to the app subnet. GO to the APP-RT --> Route --> Add route.

  ![preview](images/AWS18.png)
  ![preview](images/AWS19.png)
   


