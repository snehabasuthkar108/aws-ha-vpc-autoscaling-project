# Security Groups Design

## Overview
Security Groups are used as virtual firewalls to control inbound and outbound traffic
to AWS resources in this architecture.

## Application Load Balancer Security Group

### Inbound Rules
| Protocol | Port | Source | Description |
|--------|------|--------|-------------|
| HTTP | 80 | 0.0.0.0/0 | Allow internet traffic |
| HTTPS | 443 | 0.0.0.0/0 | Secure internet traffic |

### Outbound Rules
| Protocol | Port | Destination | Description |
|--------|------|------------|-------------|
| All | All | EC2 Security Group | Forward traffic to instances |

## EC2 Instances Security Group

### Inbound Rules
| Protocol | Port | Source | Description |
|--------|------|--------|-------------|
| HTTP | 80 | ALB Security Group | Allow traffic only from ALB |

### Outbound Rules
| Protocol | Port | Destination | Description |
|--------|------|------------|-------------|
| HTTPS | 443 | S3 Prefix List | Access S3 via VPC Endpoint |
| All | All | VPC CIDR | Internal communication |

## Design Considerations
- EC2 instances do not allow direct internet access
- Only ALB can communicate with EC2 instances
- Principle of least privilege is followed
- Security Groups are stateful

