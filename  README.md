This project involves creating a highly available serverless application that spans multiple AWS regions with disaster recovery capabilities. The architecture shown in  diagram demonstrates an active/active or active/passive setup using AWS serverless services.

Architecture Overview
Multi-Region Deployment: The application is deployed in two AWS regions (Region A and Region B)

Frontend: S3 hosts a static website (frontend) with Route 53 for DNS routing

Backend: API Gateway provides REST APIs that trigger Lambda functions

Database: DynamoDB with global tables for cross-region replication

Failover: Route 53 can route traffic to either region based on configuration
