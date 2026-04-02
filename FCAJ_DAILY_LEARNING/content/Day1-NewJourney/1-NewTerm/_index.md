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
