---
title: "New Terms"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Here I'll note down some new AWS or programming terms that I'm not yet fully familiar with.

- **DC (Data Center)**: The place where AWS stores its servers, optimized to deliver the best possible performance.
- **AZ (Availability Zone)**: 1 AZ consists of 1 or more DCs. AZs are designed to be independent from each other during failures, but interconnected during normal operation. There are dedicated high-speed connections between AZs.
- **Region**: 1 Region consists of 3 or more AZs. Regions are connected to each other via the backbone network. Data and services between Regions are isolated from each other.
- **Edge Locations (POP)**: A network of nodes that provides edge networking services (CloudFront CDN, WAF, Route 53 DNS).
- **CloudFront CDN**: Content Delivery Network — caches frequently accessed data so that users can access it faster.
- **WAF (Web Application Firewall)**: A layer of protection for websites, helps mitigate DDoS attacks.
- **Route 53**: Used to create domains and attach SSL/TLS certificates to them.
- **Serverless**: Services that don't require managing a server (e.g., creating databases, designing APIs, etc.).
- **AWS Budget**: A service to monitor and manage the cost of using AWS services.

- **Amazon VPC (Virtual Private Cloud)**: A private network space that allows you to launch AWS resources into a defined virtual network.
    + A VPC resides within a single Region and must have an IPv4 CIDR block when created.
    + Limit: 5 VPCs per Region per Account.
    + Purpose: To separate environments (Production / Dev / Test / Staging).
    + A VPC allows creating multiple virtual networks and dividing them into smaller sub-networks → Subnets.
    + **VPC Subnet**: Resides within a specific AZ; the Subnet CIDR is a sub-network of the VPC CIDR.

- **Route Table**: A collection of routes used to determine the path for network traffic.
    + When a VPC is created, a Default Route Table is automatically created (it allows all Subnets within the same VPC to communicate with each other). The Default Route Table cannot be deleted.
    + Route Tables are associated with Subnets.
    + Custom Route Tables can be created as needed.

- **ENI (Elastic Network Interface)**: A virtual network card that is preserved when switching servers (retaining Private IP, Elastic IP, and MAC address).
- **EIP (Elastic IP Address)**: A static IPv4 address that can be associated with an ENI.

- **VPC Endpoint**: Enables resources within a VPC to connect to AWS Services via AWS PrivateLink (without requiring an Internet connection).
    + **Interface Endpoint**: Uses an ENI within the VPC and a Private IP to connect to Services.
    + **Gateway Endpoint**: Uses the Route Table to route traffic to Services (supports DynamoDB & S3).

- **Internet Gateway**: A VPC component that allows EC2 Instances within the VPC to communicate with the public Internet; managed by AWS.
- **NAT Gateway**: Allows EC2 Instances within a Subnet to access the Internet or other AWS Services. Only allows outbound traffic — inbound connections are not permitted.

- **Security Group (SG)**: A **stateful** virtual firewall that inspects inbound and outbound traffic for AWS resources.
    + SG rules are restricted by: Protocol, Source Address, Connection Port, and other SGs.
    + SG rules only support **allow** rules (no explicit deny).
    + SGs are applied to ENIs.

- **Network Access Control List (NACL)**: A **stateless** virtual firewall that controls inbound and outbound traffic for AWS resources.
    + NACL rules are restricted by: Protocol, Source Address, and Connection Port.
    + NACLs are applied to VPC Subnets.
    + By default, a NACL allows all inbound and outbound traffic.

- **VPC Flow Logs**: Captures information about the IP traffic going to and from ENIs in a VPC.
    + Log files can be exported to CloudWatch Logs or S3.
    + VPC Flow Logs do **not** capture the content (payload) of packets.

- **VPC Peering**: Enables connectivity between 2 or more VPCs so that resources within those VPCs can communicate without going through the Internet.
    + VPC Peering is a 1:1 connection between two VPCs; transitive routing is **not** supported.
    + VPC Peering is **not** supported when the two VPCs have overlapping IP address ranges.

- **Transit Gateway (TGW)**: Connects multiple VPCs and on-premises networks through a central hub, simplifying network topology.
    + **Transit Gateway Attachment (TGA)**: The mechanism used to attach a subnet from each VPC to a TGW.
    + TGA operates at the AZ level.
    + Within a VPC, if one Subnet in an AZ has a TGA to a TGW, all other Subnets in the same AZ can also reach the TGW.

- **VPN Site-to-Site**: Used in hybrid architectures to maintain a persistent connection between an on-premises environment (Data Center) and an AWS VPC.
    + **Virtual Private Gateway**: Fully managed by AWS (splits into 2 endpoints across 2 AZs).
    + **Customer Gateway**: The endpoint on the customer side (Hardware Device or Software Appliance).

- **VPN Client-to-Site**: Allows a single host to access resources within a VPC. Recommended: Use a VPN Client-to-Site solution from the AWS Marketplace.

- **AWS Direct Connect**: A service that provides a dedicated network connection from a traditional Data Center to AWS (typical latency: 20ms – 30ms).
    + Operates in two forms: **Hosted Connections** and **Dedicated Connections** (bandwidth can be adjusted).
