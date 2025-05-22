This project involves creating a highly available serverless application that spans multiple AWS regions with disaster recovery capabilities. The architecture shown in  diagram demonstrates an active/active or active/passive setup using AWS serverless services.

Architecture Overview
Multi-Region Deployment: The application is deployed in two AWS regions (Region A and Region B)

Frontend: S3 hosts a static website (frontend) with Route 53 for DNS routing

Backend: API Gateway provides REST APIs that trigger Lambda functions

Database: DynamoDB with global tables for cross-region replication

Failover: Route 53 can route traffic to either region based on configuration
7

### **Step 1: Set Up DynamoDB Global Tables**
DynamoDB Global Tables provide automatic multi-region replication.

### **Step 2: Create IAM Roles for Lambda Functions**
Lambda functions need permissions to interact with DynamoDB.

### **Step 3: Create Lambda Functions in Both Regions**
We’ll create two Lambda functions in Python: one for reading data and one for writing data.


### **Step 4: Set Up API Gateway in Both Regions**
Create REST APIs to expose the Lambda functions.

### **Step 5: Create ACM certificates and custom domain for the APIs**
We need a custom domain for our APIs along with SSL/TLS certificates before we can create the Route 53 records.

### **Step 6: Set Up Route 53 DNS Name**
Now that the APIs exist, we’ll create a DNS name (e.g., `api.example.com`) that points to the active region.

### **Step 7: Create the Frontend Website**
The frontend will use HTML, Bootstrap for styling, and JavaScript to interact with the API.


### **Step 8: Test the Failover Mechanism**
1. **Simulate a Failure**:
- Delete the API Gateway in the primary region.
- Route 53 health checks will detect the failure and route traffic to the secondary region.
2. **Verify the Frontend**:
- The frontend will continue to work seamlessly, as it uses the Route 53 DNS name to connect to the active region.
