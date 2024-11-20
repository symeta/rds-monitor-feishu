# rds-monitor-feishu
- objective: to achieve acquiring RDS monitoring alerts via Feishu

## solution diagram

<img width="821" alt="image" src="https://github.com/user-attachments/assets/66386591-8ecf-4f6c-9007-64a883c333ab">

## implementation guidance

### 1. install and config Feishu Notifier via aws console

- navigate to Serverless Application Repository console and search for "notifier", do toggle "Show apps that create custom IAM roles or resource policies"


<img width="1354" alt="Screenshot 2024-11-20 at 12 34 06" src="https://github.com/user-attachments/assets/29ad975c-4839-405a-92e4-30183a6a5ffa">


- click Feishu Notifier and enter Webhook URL in corresonding dialog box and deploy the serverless application.

<img width="494" alt="Screenshot 2024-11-20 at 12 35 23" src="https://github.com/user-attachments/assets/436b68ed-0e9d-48ef-bdc6-74d785c8269a">


- the deployment will trigger an execution of a cloudformation template.

<img width="1432" alt="Screenshot 2024-11-20 at 12 37 22" src="https://github.com/user-attachments/assets/e8753555-7458-4ab8-beb1-a9438b7261fd">

- switch to "Outputs" tab of the cloudformation template, and get the SnsTopicArn

<img width="933" alt="Screenshot 2024-11-20 at 12 40 08" src="https://github.com/user-attachments/assets/c591e753-ad06-47d2-8cb9-ab397ddb2bdf">

### 2. config rds monitoring and alert

- navigate to rds console, enter into a rds for mysql instance dashboard, and switch to "Logs&events " tab.

<img width="1215" alt="Screenshot 2024-11-20 at 12 43 28" src="https://github.com/user-attachments/assets/4f6272e1-9294-4e07-9555-c754410e20c1">

- click "Create Alarm" button to create an alerm

<img width="1040" alt="Screenshot 2024-11-20 at 12 44 26" src="https://github.com/user-attachments/assets/a15c5c5a-2515-419f-9462-64563e89054b">

- make sure the SNS topic ARN is the same with the one that has been acquired from step1.

- choose the monitoring metrics, threshold, evaluation period that are needed by business, and create the alarm



