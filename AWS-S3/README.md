# S3(Simple Storage Service)
* If I want a storage for EC2 level, VPC level or I wantto share this data with other VPC pr for other Account users or I want a storage to access by the people from world wide web(WWW). If I need a storage where I can attach to my local computer. This is where we gonna use **`S3`**.
* S3 is a scalable services there is no particular limit on how much data you want to store.
* S3 is a global service(not region specific)
* It is a metered service(Pay as per the amount stored)
* _**AWS S3** is an object storage service that offers industry leading scalability, data availability, security and performance. You can use Amazon S3 to store &retrive any amount of data at any time from anywhere._
* S3 is a serverless storage. No need of any server to store the data.

### S3 Components
1. Buckets
2. Objects
3. Bucket settings
4. ACL settings
5. Versioning
6. Static Web Hosting with S3
7. Replications
8. Lifecycle Policies

#### 1. Buckets
##### Creation of a S3 Bucket
1. **Bucket Name:** Bucket name should be globally unique(like an email) and should follow the limitations set.

![preview](images/storage24.png)
![preview](images/storage25.png)

2. **Object Ownership:** Ownership is nothing but who has to access to modify, delete or control on the objects that are going to store which has ACL(Access control list)
   
![preview](images/storage26.png)

3. **Public Access Settings:** If you want to share the objects with the people from outside world we have allow.

![preview](images/storage27.png)

4. **Bucket Versioning:** Keeping multiple varients of same object in a single bucket.

![preview](images/storage29.png)

5. **Encryption:** If bucket key is enabled then S3 will go aheat and creates its own key

![preview](images/storage28.png)
![preview](images/storage30.png)

#### 2. Objects
* Objects are fundametal entities stored in AWS S3.
* There is no limit for the number of objects that you can upload.
* The size of each object should not exceed 5TB.
  
  ![preview](images/storage31.png)
  ![preview](images/storage32.png)

* We can upload files or folders by drag and drop or by clicking add files or add folders.

  ![preview](images/storage33.png)

* I uploaded different types of files and there type can be seen beside.
* We can upload any type of files(code,images,documents,videos)
* Every object will have individual URL.
  
  ![preview](images/storage34.png)

* Copy the URL and browser in chrome.
  
  ![preview](images/storage35.png)

#### 3. Bucket settings
* Access is denied because I have blocked all public access.
  
  ![preview](images/storage36.png)
  ![preview](images/storage37.png)
  ![preview](images/storage38.png)

* Edit the object ownership.
  
  ![preview](images/storage39.png)
  ![preview](images/storage40.png)
  ![preview](images/storage41.png)

#### 4. ACL Settings
* Here we can give permissions to bucket owners, Everyone(Public Access),Authenticated users Group(Anyone with an AWS group)
  
  ![preview](images/storage42.png)
  ![preview](images/storage43.png) 

* We can give access to other aws account.

 ![preview](images/storage44.png)

* Now try to access the object in browser.
* Above settings are bucket level.
* Now we have to select object --> Actions --> Make public using ALCs --> Make public
  
  ![preview](images/storage45.png)
  ![preview](images/storage46.png)

* Now refresh the link of object
  
  ![preview](images/storage47.png)

* Ratherthan going through this settings, S3 is providing pre-assigned URL.
  
  ![preview](images/storage48.png)
  ![preview](images/storage49.png)
  ![preview](images/storage50.png)
  ![preview](images/storage51.png)

* S3 will create a custom URL. this Url will last for 12hr or until your session expires.
* It will give an URL then we can access the file.
* This the link of pre-assigned url 
```
https://tteokbokki-in.s3.us-east-1.amazonaws.com/3042473-uhd_3840_2160_30fps.mp4?response-content-disposition=inline&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEEsaCXVzLWVhc3QtMSJHMEUCIQCiD5pLe%2ByPBFjrZ44prjpTzC8f6zp35b8KXb4VnOp%2BQAIgP6lpb7Kp4mt0xB5cCdUUiFiUnch83dWeDOe4FqD4gzwq5wMI1P%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAAGgwzODE0OTIxOTQ2MTciDMcthAgXpjojOQl3hiq7Az09eAeH6ix%2FnUzgtJEeTXHrzpof5%2F2hd8xGpgIhqy54xmxcYXEYDCFeITsxXZV1fRDey5KZnZcXxPpvRY5QlojsCHiFYg15Ug7DmuAlLuVZl81QzOeOQvw%2BldLjgmx6Yt8TTOAL%2BX1bK8Y4t4robwz9bskwc7hhTuDd7Mq1AswChPFepXts1oiNC56X63h9AJS2gRnkQF0EVmR23P7F7kTy3QsACm8RT%2FGUGqHSELP3%2FlUIQ4geKEpa6r3T8haGXYx7SkxtawLX8lf2Mv5QiNXtO7rx%2FoHtuSt21tHrrvqpWBHCGMhB8fQLlFZqjPjtf5A53kHIDszwMpMdwJrGJaHwgwTiVJTEcXOKHhr9doUr3n20f09%2Bqv69EeEnKWjVMubYurbeQBiheK0jJh53AQ4gGM%2B6J1r4XqPqhmEPk%2BimQ1HUcP%2Bvcnzx5pK1bDZbILJqbe0kOIiy1lUSBQ4eFFWpdD69RgNXIa%2B6mOMP6Zp9V0ESjApWNsGCfIKpfgRMBJlMppdzQF8sYRk7wkwnSM2JqM45ZReH7ol1bklSpaYYhsoD0Ts52lmkn1k9ZY%2FwAA22RrKl9PRROpCHMMHQ0bkGOuQCpRha6ltHAzaSAmID5GBnwqzoH87YtINnI%2Fn9CjclC8ApkJfNUcQnAmeznZV6EnK64TWFYVG3QCztvdNWMeRqkIL9pSeztM9PP%2FeV3KeO8kFQIlTfQuBslLdIeHDr5MOobqxcndGsP1eeBbqcnnA%2FnDw2FOLcMRqEJPGZXubTvRnzQ%2FR%2BPIOGhC2WNGQVenQL6PsPNvilhNRpdWPtpsnkvzzi50vVqFjOOx2D59YVzawwCOamptKmtdYbBuCtWdvsbG%2FwWNaKnhEWCrBzVLXv1PW1SReJ5WRhckaRg0sWJp%2Fd7hhEP1fD8yyfLW%2FJPuSjcmYqsmQ4NlheooXbvq9mYjDQ9g4nO7Kd9UjzdFxptFV4u4xI565UruFaM7tLSkrvm8VJUSsKhlnhPESaLNEHMWyYsXevyJHEDvKdpKUb7EU5rfvXEC9tFZY8vY7WlvjzYMynR1VXAryGrhlH4%2BIJWVSNnyo%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAVRUVU5U46CWILCE4%2F20241113%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241113T104131Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=7b2f9d8349436ee38e6e5cc868d8f021363e7ba69a2fca8cf25f66c9d62e74ea
```
* This is the link for object url
```
https://tteokbokki-in.s3.us-east-1.amazonaws.com/3042473-uhd_3840_2160_30fps.mp4
```

#### 5. Bucket Versioning
* Try to delete an object from S3 bucket.
  
  ![preview](images/storage56.png)
  ![preview](images/storage57.png)

* it means of keeping multiple variants of an objects you can use versioning to presence, retrive and restore every versioning of every object stored in your S3
* Select Bucket --> Properties --> Bucket Versioning (Suspend --> Enabled)
  
  ![preview](images/storage52.png)
  ![preview](images/storage53.png)
  ![preview](images/storage54.png)

* After enabling versioning, In object there will be an option like show version(this swtich should always in off)
  
  ![preview](images/storage55.png)

* After enabling versioning, delete an object.
  
  ![preview](images/storage58.png)
  ![preview](images/storage63.png)

* Before versioning I have entered `Permanently delete`. But after versioning It is asking only delete.
* If I `on` the versions switch It will show all the versions of the objects. Deleted objects will have a extra file with delete marker.

  ![preview](images/storage59.png)

* If you want to recover the files which were deleted then just delete the objects which have delete marker.  
  
  ![preview](images/storage60.png) 
  ![preview](images/storage61.png)
  ![preview](images/storage62.png)

#### 6. Static Web Hosting
* We can store the code in S3 and later deploy the code as a website. This only works for static web.
* Dynamic needs building(code has to be converted to  package) we can not do that on S3
* For an application,it has different files and each file will have diffeent URL then which URL we have to browse. So S3 has given an option to create a uniquw link that can be used for typical web hosting link

  ![preview](images/storage63.png)
  ![preview](images/storage64.png)
  ![preview](images/storage65.png)
  ![preview](images/storage66.png)
  ![preview](images/storage67.png)
  ![preview](images/storage68.png)
  ![preview](images/storage70.png)

```json 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::tteokbokki-in/*"
        }
    ]
}
```
* Copy the URL given by static web hosting 
  
  ![preview](images/storage69.png)


#### Replications
* We always store the data close to customers location, So we will maintain a replication of bucket over customers location.
  
  ![preview](images/storage71.png)
  ![preview](images/storage72.png)
  ![preview](images/storage73.png)
  ![preview](images/storage74.png)
  ![preview](images/storage75.png)
  ![preview](images/storage76.png)
  ![preview](images/storage77.png)
  ![preview](images/storage78.png)
  ![preview](images/storage79.png)
  ![preview](images/storage80.png)
  ![preview](images/storage81.png)
  

* This is the policy inline provided by AWS.
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:InitiateReplication"
            ],
            "Resource": "arn:aws:s3:::tteokbokki-us-east-1/*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion"
            ],
            "Resource": [
                "arn:aws:s3:::{{ManifestDestination}}/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::tteokbokki-us-west-2/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetReplicationConfiguration",
                "s3:PutInventoryConfiguration"
            ],
            "Resource": "arn:aws:s3:::tteokbokki-us-east-1"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::{{ManifestDestination}}/*"
        }
    ]
}
```
![preview](images/storage82.png)
![preview](images/storage83.png)

#### Life Cycle Rules
* Generally, when we store files in S3 by default it will provide standard class.
* Files which don't want to store forever in S3. We can set an expiration for those kind of files using Life cycle rules.
* Lifecycle rules in Amazon S3 are used to manage the lifecycle of objects in a bucket. 
* These rules automate the transition of objects to different storage classes, expiration of objects, or deletion of incomplete multipart uploads. 
* Lifecycle rules help optimize costs and manage data retention efficiently.

##### Key Features of S3 Lifecycle Rules
1. Transition Actions:

      * Move objects between storage classes (e.g., from S3 Standard to S3 Glacier).
2. Supported transitions:
     * S3 Standard → S3 Standard-IA or S3 Intelligent-Tiering.
     * S3 Standard-IA → S3 Glacier Instant Retrieval, S3 Glacier Flexible Retrieval, or S3 Glacier Deep Archive.
3. Expiration Actions:

      * Permanently delete objects after a specific period.
      * Can apply to specific object versions in versioned buckets.
4. Abort Incomplete Multipart Uploads:

     * Automatically delete incomplete multipart uploads after a specified number of days.
5. Filter-Based Rules:

     * Apply rules based on object prefixes or tags for fine-grained control.
##### Example Use Cases
1. Cost Optimization:

      * Move infrequently accessed data to S3 Standard-IA or S3 Glacier to reduce costs.
2. Data Retention Policy:

      * Automatically delete logs or temporary files after 90 days.
3. Data Archiving:

      * Transition older backups to S3 Glacier Deep Archive for long-term storage.

##### S3 Storage Classes

1. S3 Standard: For frequently accessed data.
2. S3 Intelligent-Tiering: For data with unpredictable access patterns.
3. S3 Standard-IA (Infrequent Access): For infrequently accessed data.
4. S3 One Zone-IA: For infrequent access data with low resilience needs.
5. S3 Glacier: For archival data with retrieval times from minutes to hours.
6. S3 Glacier Deep Archive: For long-term archival with retrieval times in hours.
7. S3 Reduced Redundancy Storage (RRS): Deprecated and no longer recommended.

##### Steps to Create S3 Lifecycle Rules

* Open the S3 Management Console.

* Select the Bucket: Choose the bucket for which you want to apply lifecycle policies.
* Go to the Management Tab: Under your bucket settings, select the Management tab.
  
  ![preview](images/storage84.png)

* Create Lifecycle Rule:

* Add Rule: Choose whether you want to create a new rule or modify an existing one.
* Configure the Rule: You can define conditions such as:
   * Prefix (specific folders or objects)
   * Tags (e.g., only objects with a specific tag)
   * Object Age (e.g., older than 30 days)
  
![preview](images/storage85.png)

* Set Actions:

   * Transition Actions: Move to another storage class after a certain number of days.
   * Expiration Actions: Delete objects after a certain number of days.
   * Noncurrent Version Expiration: Delete older versions of objects in versioned buckets.
   * Abort Multipart Uploads: Abort uploads that have been incomplete for a specified period.
  
  ![preview](images/storage86.png)
  ![preview](images/storage89.png)
  ![preview](images/storage87.png)
  
* Review and Save: Review your settings and save the lifecycle rule.
  
  ![preview](images/storage88.png)

##### Example of Lifecycle Rule Scenarios

1. Transition Objects to S3 Standard-IA After 30 Days
Prefix: logs/
Action: Move objects to S3 Standard-IA after 30 days.
2. Delete Objects Older Than 365 Days
Prefix: old-backups/
Action: Expire objects older than 365 days.
3. Archive Data to S3 Glacier After 180 Days and Delete After 365 Days
Prefix: archive/
