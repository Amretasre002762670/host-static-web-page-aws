
# Host a Static Website on AWS

This project demonstrates how to host a static HTML web app on AWS, utilizing various AWS services and resources to ensure scalability, reliability, and security. The setup includes deploying the web app on an EC2 instance within a Virtual Private Cloud (VPC), using an Auto Scaling Group and an Application Load Balancer to manage traffic and instances. 

## Architecture Overview

The architecture includes the following key components:

1. **VPC Configuration**: 
   - Configured a Virtual Private Cloud (VPC) with both public and private subnets across two different availability zones.
2. **Internet Gateway**: 
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.
3. **Security Groups**: 
   - Established Security Groups as a network firewall mechanism.
4. **Availability Zones**: 
   - Leveraged two Availability Zones to enhance system reliability and fault tolerance.
5. **Public Subnets**: 
   - Utilized Public Subnets for infrastructure components like the NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint**: 
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.
7. **Private Subnets**: 
   - Positioned web servers (EC2 instances) within Private Subnets for enhanced security.
8. **NAT Gateway**: 
   - Enabled instances in both the private Application and Data subnets to access the Internet via the NAT Gateway.
9. **EC2 Instances**: 
   - Hosted the website on EC2 Instances.
10. **Application Load Balancer**: 
   - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
11. **Auto Scaling Group**: 
   - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.
12. **GitHub Integration**: 
   - Stored web files on GitHub for version control and collaboration.
13. **Certificate Manager**: 
   - Secured application communications using a Certificate Manager.
14. **Simple Notification Service (SNS)**: 
   - Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.
15. **Route 53**: 
   - Registered the domain name and set up a DNS record using Route 53.

## Setup Instructions

Follow these steps to set up the project:

### Prerequisites

- AWS Account
- GitHub Account
- Registered Domain Name

### Deployment Steps

1. **Clone the Repository**
   ```bash
   git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
   cd host-a-static-website-on-aws
   ```

2. **Launch EC2 Instance and Connect**
   - Launch an EC2 instance with Amazon Linux 2 AMI in the configured VPC.
   - Connect to the EC2 instance using SSH.

3. **Run the Setup Script**

   Switch to the root user to gain full administrative privileges and execute the following script:

   ```bash
   #!/bin/bash
   # Switch to the root user to gain full administrative privileges
   sudo su
   # Update all installed packages to their latest versions
   yum update -y
   # Install Apache HTTP Server
   yum install -y httpd
   # Change the current working directory to the Apache web root
   cd /var/www/html
   # Install Git
   yum install git -y
   # Clone the project GitHub repository to the current directory
   git clone https://github.com/Amretasre002762670/host-static-web-page-aws.git
   # Copy all files, including hidden ones, from the cloned repository to the Apache web root
   cp -R host-static-web-page-aws/. /var/www/html/
   # Remove the cloned repository directory to clean up unnecessary files
   rm -rf host-static-web-page-aws
   # Enable the Apache HTTP Server to start automatically at system boot
   systemctl enable httpd
   # Start the Apache HTTP Server to serve web content
   systemctl start httpd
   ```

4. **Configure Load Balancer and Auto Scaling**
   - Set up an Application Load Balancer and target group.
   - Create an Auto Scaling Group with desired capacity and scaling policies.

5. **Set Up Domain with Route 53**
   - Register your domain and configure DNS records to point to the Load Balancer using Route 53.

6. **Secure Communications**
   - Use AWS Certificate Manager to secure application communications with SSL/TLS certificates.

7. **Set Up Notifications**
   - Configure Amazon SNS to receive notifications about Auto Scaling Group activities.

## Conclusion

Following these steps, you will have a fully functional, scalable, and secure static website hosted on AWS. This setup ensures high availability, fault tolerance, and ease of management.

For more details, refer to the provided architecture diagram and deployment scripts in the GitHub repository.

## Architecture

![Alt text](/Host_a_Static_Website_on_AWS.png)
