# aws-secure-multi-tier-vpc-architecture
Designed and implemented a secure, highly available multi-tier AWS VPC architecture across two Availability Zones using Public, Application, Middleware, and Database subnets, with custom Route Tables, Internet Gateway, NAT Gateways, Security Groups, and Network ACLs.
# Secure Multi-Tier AWS VPC Architecture

## Project Overview

This project demonstrates the design and implementation of a secure, scalable, and highly available multi-tier network architecture on Amazon Web Services (AWS).

The architecture is deployed inside a custom VPC across two Availability Zones (AZs) in the Mumbai region (`ap-south-1`).

The VPC is divided into four subnet tiers: Public, Application, Middleware, and Database. Each tier is designed with specific network access requirements to improve security, isolation, and availability.

## AWS Services Used

- Amazon VPC
- Public and Private Subnets
- Internet Gateway (IGW)
- NAT Gateways (2 AZs)
- Route Tables
- Security Groups
- Network ACLs (NACLs)
- Availability Zones
- IPv4 CIDR Planning

## Network Architecture

| Component | Configuration |
|---|---|
| VPC Name | devops-project-vpc |
| Region | Mumbai (ap-south-1) |
| VPC CIDR | 10.0.0.0/17 |
| Availability Zones | ap-south-1a, ap-south-1b |
| Total Subnets | 8 |
| Public Subnets | 2 |
| Application Subnets | 2 |
| Middleware Subnets | 2 |
| Database Subnets | 2 |
| Internet Gateway | 1 |
| NAT Gateways | 2 |

## Subnet Configuration

| Subnet Tier | Availability Zone | CIDR Block |
|---|---|---|
| Public | ap-south-1a | 10.0.0.0/25 |
| Public | ap-south-1b | 10.0.0.128/25 |
| Application | ap-south-1a | 10.0.8.0/21 |
| Application | ap-south-1b | 10.0.16.0/21 |
| Database | ap-south-1a | 10.0.24.0/23 |
| Database | ap-south-1b | 10.0.26.0/23 |
| Middleware | ap-south-1a | 10.0.32.0/22 |
| Middleware | ap-south-1b | 10.0.36.0/22 |

## Security Implementation

### 1. Network ACLs (NACLs)

Created separate custom Network ACLs for each subnet tier:

- Public NACL
- Application NACL
- Middleware NACL
- Database NACL

Configured inbound and outbound rules to control traffic between subnet tiers.

### 2. Security Groups

Designed Security Group rules to restrict access between application components.

- Public tier: Web traffic (HTTP/HTTPS).
- Application tier: Application traffic from approved sources.
- Middleware tier: Redis, Kafka, and Elasticsearch-related ports, as required.
- Database tier: MySQL and MongoDB-related ports, as required.

### 3. Network Routing

- Internet Gateway for public subnet internet connectivity.
- Two NAT Gateways for private subnet outbound internet access.
- Separate route tables for subnet traffic management.
- Database subnets use local VPC communication without a default internet route.

## Key Learning Outcomes

- Designed a multi-tier AWS VPC architecture.
- Practiced IPv4 CIDR and subnet planning.
- Configured public and private subnet routing.
- Implemented Internet Gateway and NAT Gateway connectivity.
- Created custom Network ACLs with inbound and outbound rules.
- Applied Security Group-based access control.
- Understood network isolation across two Availability Zones.

## Project Objective

The objective of this project is to understand how real-world AWS network infrastructure is designed, segmented, secured, and managed using AWS networking services.

## Future Improvements

- Deploy EC2 instances in each tier.
- Configure an Application Load Balancer.
- Implement VPC Flow Logs.
- Automate infrastructure using Terraform.
- Configure monitoring using Amazon CloudWatch.

## Author

AWS Cloud & DevOps Learner

## Disclaimer

This is a hands-on learning project created for AWS networking and cloud infrastructure practice. It demonstrates network architecture and security configuration; application workloads and production-level high availability can be added as future improvements.
