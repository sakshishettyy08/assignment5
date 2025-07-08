# Setup For ALB 

**Create Target Groups**
- select Instance 
- Target group name: TG-Web 
- select VPC which is yours


**Create ALB**
- Load balancer name: Sakshi-assignment5
- VPC: custom-vp-sakshi
- AZ: 
    - us-east-1a
    - us-east-1b
- security groups: sakshi-load-balancer-sg
- listeners: HTTPS 443 TG-Web-Sakshi
- SSL/TLS: ACM *.aditya-dev-com
- add rule 
    - Condition: Path is /admin/*
    - Action: Forward to TG-Admin
    - Priority: 1

    - Condition: Path is /api/*
    - Action: Forward to TG-API
    - Priority: 2

# Steup ASG

**Create Launch Template**
- Name the lauch template: sakshi-lauch
- Select the AMI: Amazon Linux
- Select Instance type
- Select key pair 
- select your subnet 
- in advance details put the user data if there

**Create ASG**
- Name the auto scaling group name
- Select Lauch Template: sakshi-lauch
- select the no. of vCPUs 2 min and 4 max
- select memory 1 min and 2 max
- vpc: custom-vp-sakshi
- select the option existing load balancer 
- then select the target group of yours 
- add notification through sns 
- add tags

# Validating Funcionality and Testing
- in the lauch template add the stress 
- check the instances if its usage goes up 
- check the health monitor to see if the instance is healthy or not


