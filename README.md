# AWS Web Application Architecture Design

## Project Overview

This project presents a conceptual design of a highly available, scalable, and secure web application infrastructure using Amazon Web Services (AWS).

The architecture demonstrates how AWS networking, compute, database, and storage services can work together to support a modern multi-tier web application.

## Architecture Components

- **Amazon VPC:** Provides an isolated network environment using CIDR block `10.0.0.0/16`.
- **Availability Zones:** Uses two Availability Zones to improve availability and resilience.
- **Internet Gateway:** Enables internet connectivity for public-facing resources.
- **Application Load Balancer (ALB):** Distributes incoming application traffic across frontend servers.
- **Amazon EC2:** Hosts frontend and backend application servers in private subnets.
- **Amazon RDS:** Provides a relational database with a Multi-AZ standby configuration for high availability.
- **Amazon S3:** Provides scalable object storage.
- **NAT Gateways:** Allow private subnet resources to initiate outbound internet connections.
- **S3 Gateway VPC Endpoint:** Enables private access to S3 through AWS networking without requiring NAT for S3 traffic.

## Network Design

The VPC is divided into public and private subnets across two Availability Zones.

- Public subnets host the internet-facing load balancer and NAT Gateways.
- Private web subnets host frontend EC2 instances.
- Private application subnets host backend EC2 instances.
- Private database subnets host the RDS database resources.

## Scalability and High Availability

The architecture supports horizontal scaling by adding more EC2 instances when application demand increases.

Application Load Balancers distribute traffic across healthy targets. The Multi-AZ database configuration supports database failover, while deploying NAT Gateways in both Availability Zones reduces cross-zone dependencies.

## Security Considerations

- Apply least-privilege access through AWS IAM.
- Use security groups to restrict communication between application tiers.
- Use HTTPS for public application traffic.
- Keep application and database servers in private subnets.
- Encrypt data at rest and in transit.
- Store sensitive credentials securely.
- Monitor infrastructure using Amazon CloudWatch.

## Performance Considerations

- Use load balancing to distribute traffic.
- Scale EC2 instances horizontally.
- Consider Amazon CloudFront for content delivery.
- Consider Amazon ElastiCache for frequently accessed data.
- Monitor application and infrastructure performance.

## Project Documentation

The detailed architecture report is available here:

`documentation/aws_web_application_architecture_report.pdf`

## Project Status

**Status:** Conceptual architecture design completed.

This project is intended for learning and portfolio development. The infrastructure has not yet been deployed or tested in AWS.

## Author

**Charles Mukasa Luyinda**

Cloud Engineering and DevOps Learner

GitHub: [@cmluyinda](https://github.com/cmluyinda)
