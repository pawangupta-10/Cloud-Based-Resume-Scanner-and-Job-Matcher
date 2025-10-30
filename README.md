☁️ Cloud-Based Resume Scanner and Job Matcher

A scalable cloud platform that enables users to upload resumes, automatically extract candidate information using Amazon Textract, and match skills and experience to job listings stored in an Amazon RDS (MS-SQL) database. The system uses AWS Lambda for serverless compute, API Gateway for API management, and provides secure access, monitoring, and analytics via AWS services.

🧩 Architecture Overview

The project follows a three-tier architecture:

1. Presentation Tier:

  - Amazon S3 – Hosts the static frontend web app.
  - Amazon CloudFront – Delivers static content globally via CDN.
  - Amazon Cognito – Handles user authentication and authorization.
  - AWS WAF (Web Application Firewall) – Protects the application from common web exploits.

2. Logic Tier:

  - Amazon API Gateway – Exposes REST endpoints for frontend-backend communication.
  - AWS Lambda Functions – Handles core logic:
      - UploadResumeFn – Processes resume uploads and triggers Textract.
      - TextractCallbackFn – Receives Textract results and stores extracted data.
      - MatchJobsFn – Compares extracted candidate skills with job database entries.
  - Amazon SNS – Sends notifications after successful job matching.


3. Data Tier:

  - Amazon Textract – Extracts structured data (name, skills, experience) from uploaded PDFs.
  - Amazon RDS (MS-SQL) – Stores job listings and extracted candidate information.
  - Amazon CloudWatch – Monitors application performance and logs Lambda executions.
  - Amazon QuickSight – Provides dashboards for analytics and insights (e.g., most in-demand skills, job match trends).

⚙️ Key Features

  - Resume text extraction using Amazon Textract.
  - Skill and experience matching against job listings in RDS.
  - Serverless architecture for high scalability and low maintenance.
  - Secure authentication and DDoS protection with Cognito and WAF.
  - Analytics dashboard built with Amazon QuickSight for visual insights.
  - CloudWatch logging and SNS notifications for system observability.

🏗️ AWS Services Used

  - Storage & Hosting -	Amazon S3, CloudFront
  - Security & Auth	- Cognito, WAF
  - Compute & API	- Lambda, API Gateway
  - Database	- Amazon RDS (MS-SQL)
  - AI/ML Processing	- Amazon Textract
  - Monitoring & Alerts	- CloudWatch, SNS
  - Analytics	- Amazon QuickSight

🚀 Workflow

  1. User uploads a resume via the web interface (S3 + CloudFront).
  2. The resume triggers API Gateway, invoking a Lambda function.
  3. The function stores the resume in S3 and calls Amazon Textract.
  4. Extracted data (skills, experience, education) is processed and inserted into RDS.
  5. MatchJobsFn compares candidate data with job listings and returns top matches.
  6. SNS sends email notifications to users with match results.
  7. QuickSight visualizes data trends and performance metrics.
