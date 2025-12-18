# Application Load Balancer & Auto Scaling Group Design

## Application Load Balancer (ALB)

### Overview
The Application Load Balancer is deployed in public subnets across two Availability Zones
to distribute incoming traffic to EC2 instances running in private subnets.

### Listener Configuration
| Listener Port | Protocol | Action |
|--------------|----------|--------|
| 80 | HTTP | Forward to Target Group |
| 443 | HTTPS | Forward to Target Group (optional) |

### Target Group
- Target Type: Instance
- Protocol: HTTP
- Port: 80
- Health Check Path: /health
- Health Check Interval: 30 seconds

---

## Auto Scaling Group (ASG)

### Overview
The Auto Scaling Group manages EC2 instances across private subnets in two Availability Zones
to ensure high availability and scalability.

### Capacity Configuration
| Setting | Value |
|-------|-------|
| Desired Capacity | 2 |
| Minimum Capacity | 1 |
| Maximum Capacity | 4 |

### Scaling Policies
- Scale out when average CPU utilization > 60%
- Scale in when average CPU utilization < 30%

### Launch Configuration
- Instance Type: t2.micro
- AMI: Amazon Linux 2
- Security Group: EC2 Security Group
- User Data: Application bootstrap script

---

## Design Considerations
- ALB provides fault tolerance across AZs
- ASG ensures automatic recovery from instance failure
- Health checks prevent traffic to unhealthy instances
- Scaling policies balance performance and cost

