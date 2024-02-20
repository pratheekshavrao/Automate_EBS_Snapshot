
# Automate EBS volume backup using Lambda

To mitigate potential data loss due to instance failures or errors, EBS volumes can be safeguarded through automated backups. This involves creating snapshots, a task that can be efficiently automated using AWS Lambda functions. By scheduling Lambda execution at specific intervals, the EventBridge service facilitates the automated backup process, ensuring the timely creation of snapshots to enhance data resilience and recovery measures.


## Setup & Steps to execute

1. First create an EC2 Instance with the Target Volume. Navigate to the EC2 dashboard in the AWS console and then launch a new EC2 instance and ensure it has the relevant volume that requires backup.

2. Next to create a Lambda function,  navigate to Lambda console. Click on "Create function". Choose a meaningful name for your Lambda function, specify the runtime as Python 3.9, and create a new role.

3. Download Lambda function into AWS Cloud9 environment.In your Cloud9 environment, create two essential files: template.yaml and event.json. These files are integral for locally testing the Lambda function. 

