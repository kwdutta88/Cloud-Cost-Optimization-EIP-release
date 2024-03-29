# AWS Lambda Function for Releasing Elastic IPs

This repository contains code for an AWS Lambda function written in Python that releases unassociated Elastic IP (EIP) addresses in your AWS account.

## Overview

Elastic IPs are static public IP addresses that can be associated with various AWS resources such as EC2 instances, NAT Gateways, load balancers, and more. This Lambda function automates the process of releasing Elastic IPs that are not currently associated with any resource, helping to optimize costs and resource usage in your AWS environment.

## Functionality

The Lambda function retrieves a list of all Elastic IP addresses in your AWS account using the Boto3 SDK for Python. It then iterates through the list and releases any Elastic IPs that are not associated with any resource.

## Usage

1. Clone or download this repository to your local machine.
2. Modify the `lambda_function.py` file to include your AWS credentials and region if necessary.
3. Create an IAM role with permissions to describe and release Elastic IPs (`ec2:DescribeAddresses` and `ec2:ReleaseAddress`).
4. Create a new Lambda function in the AWS Management Console or using the AWS CLI.
5. Upload the `lambda_function.py` file as the code for the Lambda function.
6. Associate the IAM role created in step 3 with the Lambda function.
7. Optionally, configure a trigger for the Lambda function (e.g., CloudWatch Events) to automate the process of releasing unassociated Elastic IPs.

## IAM Policy

Ensure that the IAM role associated with the Lambda function has the necessary permissions to describe and release Elastic IPs. Here's an example IAM policy:


{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeAddresses",
                "ec2:ReleaseAddress"
            ],
            "Resource": "*"
        }
    ]
}
