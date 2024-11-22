# Cloud Formation
* Cloud Formation is used for building Infrastructure as a Code(IaC).
* Cloud Formation has stack. Stack is set of details you can want AWS to perform.
* AWS provide cloud formation [userguide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-formats.html).
* Cloud Formation can be written in two formates
    1. yaml
    2. json
* In stack we will give templateto create the resources. In background, templates will be stored in S3.
* We can see the overview in instructuture compose.

### Lets create a cloudformation template

* First we have to create the stack.

![preview](images/cf1.png)
![preview](images/cf2.png)
![preview](images/cf3.png)

* We can see the resources which we are going to creating.
  
![preview](images/cf5.png)
![preview](images/cf4.png)
![preview](images/cf6.png)
![preview](images/cf7.png)
![preview](images/cf8.png)
![preview](images/cf9.png)

For cloudformation template to create VPC [refer here](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/ed70e9a17a291de4265c92a18421dde5edaabd3b)

* Now we will update our infrastucture to create internet gateway, subnets, route tables.
* Extended the template to create public subnet and private subnets. [template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/836a097623ac4a29027e519dc066c39ae9f7d656)
  
* You can update the stack.
  
  ![preview](images/cf11.png)
  ![preview](images/cf12.png)
  ![preview](images/cf13.png)

* Update the stack and check the resources are created or not.
  
  ![preview](images/cf10.png)

* Now create Internet gateway and attach the internet gateway to the vpc created.[Template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/2cbd3f80b06bcd4ab5c16499864bde37599a3783)
  
* Check the resource is created or not.

![preview](images/cf14.png)
![preview](images/cf15.png)

* Now lets create two route tables.[Template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/6aa5e41edd21fdbd99e4349062bafe284f1d1d9a)

![preview](images/cf16.png)
![preview](images/cf17.png)

* Now associate subnets with Route tables respectively.[Template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/af0fc617a8e2ae63c239d22c0d10e6c5a4754ff0)
  
  ![preview](images/cf18.png)
  ![preview](images/cf19.png)
  ![preview](images/cf20.png)

* Now add route to internet gateway in public routetable.[template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/f963ef635c9553ce2649883052e8cd836d6e6e61)
  
  ![preview](images/cf21.png)
  ![preview](images/cf22.png)
  ![preview](images/cf23.png)

* Now create a security group.[template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/3ed831b341624d8ea8fdf8b23d2c845d8d2a6258)
  
  ![preview](images/cf25.png)
  ![preview](images/cf24.png)

* Now create 2 instance one in public subnet and other in private subnet.[Template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/65469dab806ca5f11c15fbd6137d018f873e3ee9)
  
![preview](images/cf26.png)
![preview](images/cf27.png)

### Parameters

_**Parameters in CloudFormation** are dynamic inputs provided during stack creation that allow you to customize resource properties without modifying the template._


1. **Reusability:** Allows the same template to work across multiple environments (e.g., Dev, Test, Prod).
2. **Customizability:** Enables dynamic configuration without modifying the template.
3. **Security:** Handles sensitive values securely (e.g., passwords or keys).
4. **Consistency:** Ensures valid inputs with constraints or default values.
5. **Flexibility:** Adapts to region-specific resources like AMI IDs or availability zones.
6. **Scalability:** Easily adjusts settings like instance types or counts for different use cases.

* Let's create a template using parameters.[Template](https://github.com/AWS-DevOps-BasicS/Cloud-Computing/commit/c1de01e2aa02d8d38b59f1f3581ad444b8e6e3e6)

![preview](images/cf28.png)
![preview](images/cf29.png)