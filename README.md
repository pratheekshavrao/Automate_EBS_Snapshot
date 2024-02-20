
# Automate EBS volume backup using Lambda

To mitigate potential data loss due to instance failures or errors, EBS volumes can be safeguarded through automated backups. This involves creating snapshots, a task that can be efficiently automated using AWS Lambda functions. By scheduling Lambda execution at specific intervals, the EventBridge service facilitates the automated backup process, ensuring the timely creation of snapshots to enhance data resilience and recovery measures.


## Setup & Steps to execute

1. First create an EC2 Instance with the Target Volume. Navigate to the EC2 dashboard in the AWS console and then launch a new EC2 instance and ensure it has the relevant volume that requires backup.

   ![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/EC2_creation_with%20_EBS.jpg)

3. Next to create a Lambda function,  navigate to Lambda console. Click on "Create function". Choose a meaningful name for your Lambda function, specify the runtime as Python 3.9, and create a new role.

   ![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/Lambda_function_created.jpg)

5. For local testing of Lambda functions, download the functions to Cloud9 environment, create event.json and template .yaml files. Use below code from terminal to test the functions.

   ![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/Local_invoke_command.jpg)
   
4. Upon successful local testing, upload the Lambda function code from Cloud9 to AWS Lambda.

5. Grant Permissions to Lambda for EC2 Access. Attach an IAM policy to the Lambda Execution Role to permit access to EC2 resources.

   ![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/Add_permissions_to_role.jpg)

7. To configure Amazon EventBridge Scheduler navigate to the Amazon EventBridge console.  Create a new schedule with a schedule expression, specifying a recurrence pattern for daily execution at a designated time.Set the scheduler’s target to be your Lambda function.

   ![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/Event_bridge_schedule.jpg)

## Result

The Scheduler will trigger the Lambda at the appropriate time and a Snapshot of the volume is created.

![alt text](https://github.com/pratheekshavrao/Automate_EBS_Snapshot/blob/master/images/Snapshot_created.jpg)

   

   

