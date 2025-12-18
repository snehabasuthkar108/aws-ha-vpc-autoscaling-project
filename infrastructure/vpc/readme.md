# VPC Design

## VPC Overview
- VPC CIDR: 10.0.0.0/16
- Region: ap-south-1
- Availability Zones:
  - ap-south-1a
  - ap-south-1b

## Subnet Design

### Availability Zone ap-south-1a
- Public Subnet: 10.0.1.0/24
- Private Subnet: 10.0.2.0/24

### Availability Zone ap-south-1b
- Public Subnet: 10.0.3.0/24
- Private Subnet: 10.0.4.0/24

## Routing Strategy

### Public Subnets
- Route to Internet Gateway (0.0.0.0/0)
- Used for Application Load Balancer

### Private Subnets
- No direct internet access
- Access to Amazon S3 via VPC Gateway Endpoint

## Design Considerations
- /16 VPC allows future expansion
- /24 subnets provide sufficient IPs for scaling
- Separation of public and private subnets improves security
- Multi-AZ setup ensures high availability

