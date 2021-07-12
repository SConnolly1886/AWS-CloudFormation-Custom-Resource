# CloudFormation-Custom-Resource
CloudFormation with custom lambda resource to delete s3 objects

![CustomeResource](https://user-images.githubusercontent.com/62077185/125342770-44a5a900-e323-11eb-98fd-5998890cda1f.png)

## CloudFormation Limitations
CloudFormation is a fantastic resource to lean on. IaaC is such an efficient way of doing things but theres only so much you can do...by default. One of the advantages of CloudFormation over Terraform is it's fine-grained control and integration with other AWS resources. With custom resources in your CloudFormation template you can do just about anything you want. Using a lambda as a custom resource is the perfect example. 

## The Problem
Deleting all of your resources in your stack is as easy as clicking delete stack. Unless, you have created s3 buckets in your template and those s3 buckets have objects in them. The stack will fail to delete completelely until you remove the objects and try deleting once more. This might seem like a small problem until you are dealing with multiple buckets or thousands of objects.

## The Solution 
Using a Custom Resource in your CloudFormation template. Create a lamba function which will trigger on requests types created by CloudFormation. Most importanltly, the Lambda will respond to the Delete request type. 

### What's will be Created?
The CloudFormation template will create:
- a generic empty s3 bucket
- Lambda function capable of deleting s3 objects and sending logs to CloudWatch
- Lamba role with permissions for CloudWatch and S3
- custom resource that references Lambda **(you can create Lambda independent from stack and reference it using its arn.)**

### Finished!
All you need to do is upload the template in this repository to try it yourself. Simply add objects to the s3 bucket and delete the stack as you normally would...but no errors! Enjoy!



