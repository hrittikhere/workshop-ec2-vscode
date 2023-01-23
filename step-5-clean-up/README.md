## Delete Resources 🧹
Using AWS CloudFormation can also help with the cleanup of resources, as you can easily delete an entire stack and all of its associated resources with a single command.

When you delete a stack, CloudFormation automatically deletes all of the resources that were created as part of the stack. This includes EC2 instances, RDS databases, S3 buckets, and more.
Additionally, CloudFormation also deletes any custom resources that you've defined in your template, ensuring that all resources created by the stack are cleaned up.

By using CloudFormation to manage your resources, you can be sure that all of the resources created by the stack are properly cleaned up when you delete the stack. This makes it easy to test and experiment with different configurations without leaving behind unwanted resources that can incur costs.


## Steps to clean 

The Step is simple as navigate to your stack page as below and click on Delete on top corner!

![Stack Page](/step-2-create-ec2/static/coudformation-stack-creation-output.png)

Click on "Delete Stack" and then confirm!

![Delete Confirmation](static/delete-cloudformation-stack.png)

Your stack with all it's resources should be deleted now!