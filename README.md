# High Availability AWS VPC with Auto Scaling

## Overview
This project demonstrates a highly available AWS architecture using a VPC across two Availability Zones.
Public subnets host the Application Load Balancer, while EC2 instances run in private subnets and are managed
by an Auto Scaling Group.

## Architecture
- VPC spanning 2 Availability Zones
- Public subnets for ALB
- Private subnets for EC2 instances
- Auto Scaling Group
- VPC Gateway Endpoint for private S3 access

## Traffic Flow
Internet → ALB → EC2 (Private Subnets) → S3 via VPC Endpoint

## Key Highlights
- High availability and fault tolerance
- Secure private subnets
- Scalable compute using Auto Scaling
- Cost-aware execution with resource teardown

## Execution Strategy
Resources were created temporarily for validation and deleted afterward to avoid ongoing cloud costs.
