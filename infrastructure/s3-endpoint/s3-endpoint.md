# S3 VPC Gateway Endpoint Design & Validation

## Overview
A VPC Gateway Endpoint is used to allow EC2 instances in private subnets
to access Amazon S3 without requiring internet access or a NAT Gateway.

## Endpoint Configuration
- Endpoint Type: Gateway
- Service: com.amazonaws.ap-south-1.s3
- Associated Route Tables: Private Subnet Route Tables

## Benefits
- Eliminates need for NAT Gateway
- Reduces operational cost
- Improves security by keeping traffic within AWS network
- Prevents exposure to public internet

## Access Control
- S3 bucket access is restricted using IAM policies
- Only EC2 instances with appropriate IAM role can access the bucket

## Validation Steps
1. Launch EC2 instance in private subnet
2. Attach IAM role with S3 access
3. Upload/download file to S3
4. Verify no internet gateway or NAT is used

## Teardown Strategy
- Delete Auto Scaling Group
- Delete Load Balancer and target groups
- Delete VPC Endpoint
- Delete subnets and route tables
- Delete VPC

## Design Considerations
- Endpoint is regional and highly available
- Works only for S3 and DynamoDB
- Keeps architecture cost-optimized

