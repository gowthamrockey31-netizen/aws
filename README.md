AI-Powered Daily Share Market Agent

An autonomous AI-powered agent built using Amazon Bedrock, AWS Lambda, Amazon EventBridge Scheduler, and Amazon SES. The agent automatically generates an Indian stock market morning report every day at 6:00 AM and sends it to the user's email without requiring any manual interaction.

📌 Project Overview

This project demonstrates how to build a serverless AI agent that runs on a schedule.

Every day at 6:00 AM, Amazon EventBridge triggers an AWS Lambda function. The Lambda function sends a prompt to Amazon Bedrock (Nova Lite), which generates an AI-powered Indian stock market report. The generated report is then emailed automatically using Amazon SES.

✨ Features
🤖 AI-generated daily stock market report
⏰ Automatic execution every day at 6:00 AM
📧 Email delivery using Amazon SES
☁️ Fully serverless architecture
🔐 Secure IAM-based permissions
📊 Execution logs available in Amazon CloudWatch
🏗️ Architecture
                Amazon EventBridge Scheduler
                      (6:00 AM Daily)
                              │
                              ▼
                       AWS Lambda
                              │
                              ▼
                Amazon Bedrock (Nova Lite)
                              │
                              ▼
             Generate Stock Market Report
                              │
                              ▼
                      Amazon SES
                              │
                              ▼
              📧 Email sent to the user
🛠️ AWS Services Used
Service	Purpose
Amazon Bedrock	AI model for report generation
AWS Lambda	Executes the application logic
Amazon EventBridge Scheduler	Runs Lambda automatically
Amazon SES	Sends the report via email
AWS IAM	Manages permissions
Amazon CloudWatch	Stores execution logs
📂 Project Structure
DailyShareMarketAgent/
│
├── lambda_function.py
├── README.md
└── screenshots/
    ├── lambda.png
    ├── eventbridge.png
    ├── ses.png
    ├── cloudwatch.png
    └── email.png
🚀 How It Works
EventBridge Scheduler triggers the Lambda function every day at 6:00 AM.
Lambda sends a prompt to Amazon Bedrock (Nova Lite).
Bedrock generates a concise Indian stock market morning report.
Lambda extracts the generated report.
Amazon SES emails the report to the verified email address.
CloudWatch stores execution logs for monitoring.
📅 Schedule

Cron Expression

cron(0 6 * * ? *)

Runs every day at 06:00 AM (Asia/Kolkata).

🧠 AI Prompt
You are a stock market analyst.

Generate a short Indian stock market morning report containing:

1. Market Overview
2. Top 3 Sectors to Watch
3. General Trading Tips

Keep it under 200 words.
📧 Sample Email

Subject

📈 Daily Share Market Report

Example Output

Indian Stock Market Morning Report

Market Overview:
The Indian stock market opened on a positive note...

Top 3 Sectors:
• Pharma
• IT
• Metals

General Trading Tips:
• Invest carefully
• Follow market trends
• Maintain diversification
🔐 IAM Permissions Required
Amazon Bedrock
{
  "Effect": "Allow",
  "Action": [
    "bedrock:InvokeModel"
  ],
  "Resource": "*"
}
Amazon SES
{
  "Effect": "Allow",
  "Action": [
    "ses:SendEmail",
    "ses:SendRawEmail"
  ],
  "Resource": "*"
}
⚙️ Deployment Steps
1. Create Lambda Function
Runtime: Python 3.12
Upload lambda_function.py
2. Configure Amazon Bedrock
Model: Amazon Nova Lite
Region: us-east-1
3. Verify Email in Amazon SES
Create a verified email identity.
Confirm the verification email.
4. Configure IAM Role

Attach permissions for:

Amazon Bedrock
Amazon SES
CloudWatch Logs
5. Create EventBridge Scheduler

Use:

cron(0 6 * * ? *)

Target:

DailyShareMarketAgent
6. Test

Click Test in AWS Lambda.

Expected response:

{
  "statusCode": 200,
  "message": "Email sent successfully!"
}
📊 Results

✅ Fully automated AI agent

✅ Daily report generation

✅ Email delivery

✅ Serverless architecture

✅ No manual intervention required

🚧 Challenges Faced
IAM permission (bedrock:InvokeModel) error
Amazon SES email verification
EventBridge Scheduler configuration
Lambda IAM role configuration

All issues were resolved by configuring the required IAM policies and verifying the SES email identity.

🔮 Future Enhancements
Integrate live stock market APIs
Store reports in Amazon S3
Send notifications via Telegram or Slack
Add investment recommendations
Create a web dashboard for report history
👨‍💻 Author

Gowtham M

Electronics and Communication Engineering (ECE)

Built using:

Amazon Bedrock
AWS Lambda
Amazon EventBridge Scheduler
Amazon SES
AWS IAM
Amazon CloudWatch
📜 License

This project is created for learning purposes and the AWS AI Agent Challenge. Feel free to fork, modify, and extend it for educational use.
