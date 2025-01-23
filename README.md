# Plush-Pages-Website
ShopPlushPages.com is designed to showcase how to build and host a fully static website on AWS with scalable and secure features. The website also incorporates CloudFront for faster content delivery and a dedicated S3 bucket for access logs.  

## Features

- **Static Website Hosting:** The site is hosted on an S3 bucket, ensuring cost-effective and scalable storage.
- **Custom Domain Name:** The domain name shopplushpages.com is managed using Route 53 for seamless DNS configuration.
- **CloudFront Integration:** A CloudFront distribution provides faster content delivery and HTTPS security.
- **Access Logging:** A dedicated S3 bucket stores CloudFront logs for tracking and monitoring.

## Architectural Diagram

![image](https://github.com/user-attachments/assets/58fcae14-6987-49c3-953d-e66470285a08)

## Setup Instructions

### Prerequisites
- AWS account with access to S3, CloudFront, and Route 53.
- A registered domain name (e.g., shopplushpages.com).

### Steps

1. Create the S3 Bucket:
  - Name the bucket shopplushpages.com.
  - Enable static website hosting and set the index document (e.g., index.html).
  - Upload all website files to the bucket.

2. Set Up Bucket Permissions:
Add a bucket policy to allow public access for website files:

        {
          "Version": "2012-10-17",
          "Statement": [
            {
              "Sid": "PublicReadGetObject",
              "Effect": "Allow",
              "Principal": "*",
              "Action": "s3:GetObject",
              "Resource": "arn:aws:s3:::shopplushpages.com/*"
            }
          ]
        }

3. Create CloudFront Distribution:
- Set the S3 bucket as the origin.
- Enable logging and specify the logging bucket.
- Use an ACM certificate for HTTPS.

Configure Route 53:
- Create a hosted zone for shopplushpages.com.
- Add an alias record pointing to the CloudFront distribution.

Test the Website:
- Open https://shopplushpages.com in a browser to verify the setup.

### Monitoring and Logs
- CloudFront logs are stored in the dedicated logging bucket for:
- Analyzing traffic patterns.
- Debugging issues.
- Tracking security-related events.

### Future Improvements
- Updating the UI 
- Add a CI/CD pipeline for automated deployments.
- Implement advanced analytics with Amazon CloudWatch.
- Introduce more dynamic functionality using serverless architectures like AWS Lambda.


