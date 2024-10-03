# Client Requirement
### IBM is our customer.
* IBM is managing there Web-Server // App // Database on Local Environment.
* IBM wants to move there application infra to the cloud.

* IBM wants there own Virtual Private network on cloud
* This network should have a capacity of 8k ip's 

#### VPC 

* IBM wants a VPC with 8k ip's
* IBM wants Internet access to the complete network
    * We should create a VPC with a cap of 8k servers
    * we should attach a IGW to this VPC

* IBM wants there network to be divided into two sub-networks
* The 1st Sub-network should be used to run Application servers
* The 2nd Sub-network should be used to run Database servers 

* The App subnet should have a capacity of 4k Servers
* The DB subnet should have a capacity of 4k Servers

#### App-Subnet

* Create a App-Subnet with 4k servers
* IBM wants IGW access to the App-Subnet
* IBM wants the app-subnet should have a public access
* The App servers should be running in the App-subnet

#### Db-Subnet

* Create a DB-Subnet with 4k servers
* IBM does not want IGW to the DB-Subnet
* The Db-Subnet should be strictly private
* The Db servers should be running in the Db-Subnet


#### Routing

* IBM wants cx from WWW to be routed to App-Subnet
* IBM wants Admins to have access to the App & DB-Subnet 

#### Route-tables

* Create Two route tables
* 1st App-Route table should be connected with IGW and App-Subnet
* 2nd DB-Route table should be connected with only DB-Subnet

**Note** - Db Rt should not be connected to the IGW

* IBM wants traffic distribution across there App-Servers
* We should create a Load-Balancer to distribut traffic across App-Servers

#### Monitoring
* IBM wants Monitoring Services for the App-Servers
If any server crashes, there should be Notification alert sent to the cx.

* Create a cloudwatch dashboard to monitor resources
Create a SNS - Simple notification service to send notification on the event of any crashes.

#### Other
* IBM wants fault-tolerance to setup for the infra
If any server crashes, AWS should be able to replace the faulty server with a new server

* IBM wants 0 downtime for the App infra 

* IBM wants a custom domain for there Application.
We will create a custom domain with R53 and integrate with the LB-DNS