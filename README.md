# CloudFormation-Custom-Resource
CloudFormation with custom lambda resource to delete s3 objects

![CustomeResource](https://user-images.githubusercontent.com/62077185/125342770-44a5a900-e323-11eb-98fd-5998890cda1f.png)

## CloudFormation Limitations
CloudFormation is a fantastic resource to lean on. IaaC is such an efficient way of doing things but theres only so much you can do...by default. One of the advantages of CloudFormation over Terraform is it's fine-grained control and integration with other AWS resources. With custom resources in your CloudFormation template you can do just about anything you want. Using a lambda function as a custom resource is a perfect example. 

## The Problem
Deleting all of your resources in your stack is usually as easy as clicking `delete stack`. Unless of course you have objects in any bucket the CloudFormation stack created. The stack will then fail to delete completely until you manually remove the objects. You must then try deleting the stack again. This might seem like a small problem until you are dealing with multiple buckets or thousands of objects.

## The Solution 
Using a Custom Resource in your CloudFormation template is a great way of dealing with this problem. Creating a lamba function which will be triggered on requests types created by CloudFormation. Most importantly, the Lambda will respond to the `Delete` request type and delete object(s) in the s3 bucket(s) which will allow the CloudFormation delete process to continue. 

### What's will be Created?
The CloudFormation template will create:
- an s3 bucket
- Lambda function capable of deleting s3 objects and sending logs to CloudWatch
- Lambda role with permissions for CloudWatch and S3
- custom resource that references Lambda **(you can create Lambda independent from stack and reference it using its arn.)**

### Finished!
All you need to do is upload the template in this repository and try it yourself. Simply add any objects you like to the s3 bucket and delete the stack as you normally would...but no errors! Enjoy!



