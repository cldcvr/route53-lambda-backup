# route53-lambda-backup

An AWS Lambda function to automatically back up Route 53 DNS records to S3.

## Setup

This script can be run either as a scheduled AWS Lambda function or as a cron job. Simply upload the script to AWS Lambda, set the `s3_bucket_name` and `s3_bucket_region` environmental variables, set up an IAM role (with Route 53 read-only and S3 read-write permissions), and set a schedule.

Alternatively, you can set the script to run using cron on an EC2 instance with the appropriate IAM role permissions. Don't forget to add the proper Python 3 shebang and set the `s3_bucket_name` and `s3_bucket_region` variables in the file when doing so.

## Restoring Backups

Backups generated by this script are uploaded as csv and json files to the specified AWS S3 bucket. They can be restored using AWS provided tools, including the AWS CLI, or using the route53-transfer module. The code and documentation for this module, including how to restore the Route 53 DNS record csv backups, can be found [here](https://github.com/RisingOak/route53-transfer).