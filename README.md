# **Spring Boot Template with Redis, JWT, and Amazon S3 Integration**

A comprehensive **Spring Boot template** designed to accelerate backend development. This template is equipped with essential features such as **Redis caching**, **JWT-based authentication**, and **Amazon S3 file management**, providing a robust foundation for building scalable and secure applications.

---

## **Features**

### 🔑 **JWT Authentication**
- Secure token-based authentication.
- Role-based access control for flexible authorization.

### ⚡ **Redis Integration**
- High-performance caching for faster data access.
- Session management to improve application scalability.

### ☁️ **Amazon S3 Integration**
- File upload, download, and management on AWS S3.
- Generate pre-signed URLs for secure file access.

### 🧩 **Advantages**
1. **Modular Design**: Easily customizable and scalable for any project.
2. **Pre-Configured Integrations**: No need to set up Redis, JWT, or S3 from scratch.
3. **Rapid Development**: Focus on features while relying on a pre-built foundation.
4. **Enhanced Security**: JWT ensures safe authentication and authorization.

### ⚠️ **Disadvantages**
1. **AWS Costs**: Amazon S3 usage may incur charges depending on your usage tier.
2. **Configuration-Dependent**: Requires careful setup of credentials in `application.properties`.

---

## **Requirements**

### Environment:
- **Java**: 23 (preferred as I used for development)
- **Maven**: 3.6+
- **Redis**: Installed and running locally or remotely
- **AWS Account**: With access to S3 bucket and IAM credentials

---

## **Configuration**

Before running the template, you must configure the following properties in the `application.properties` file:

```properties
# AWS S3 Configuration
aws.s3.access-key=YOUR_AWS_ACCESS_KEY          # AWS IAM User Access Key
aws.s3.secret-key=YOUR_AWS_SECRET_KEY          # AWS IAM User Secret Key
aws.s3.bucket-name=YOUR_BUCKET_NAME            # Name of your S3 bucket
aws.s3.region=YOUR_BUCKET_REGION               # e.g., us-east-1

# Redis Configuration
spring.redis.host=YOUR_REDIS_HOST              # Redis server hostname or IP
spring.redis.port=YOUR_REDIS_PORT              # Redis server port (default: 6379)

# JWT Configuration
jwt.secret=YOUR_SECRET_KEY                     # Secret key for signing JWT tokens
jwt.expiration=86400000                        # JWT token expiration time in milliseconds
```

---

## **How to Acquire AWS Credentials**

1. **Sign in to AWS Management Console**:
   - Go to [AWS Console](https://aws.amazon.com/console/).

2. **Create an IAM User**:
   - Navigate to **IAM** > **Users** > **Add User**.
   - Enable **Programmatic Access** and attach the policy: **AmazonS3FullAccess**.

3. **Retrieve Access Key and Secret Key**:
   - After creating the user, download the `.csv` file containing your `access-key` and `secret-key`.

4. **Set Up S3 Bucket**:
   - Go to **S3** in AWS Console.
   - Create a new bucket and note down the bucket name and region.


---

## **How to Use This Template**

### **1. Clone the Repository**
Run the following command to clone the template repository:
```
git clone https://github.com/Shivamingale3/Java-Spring-Boot-Example-Template.git
```
Open in IntelliJ Idea. 
Install dependencies using maven tool and run the main.


## **Endpoints Provided**
### **Authentication**
1. POST /auth/login: Login with credentials (username/email/mobile and password).
2. POST /auth/register: Register a new user.
3. POST /auth/logout: Logout the current authenticated user.
#### **User Management**
1. GET /users/{id}: Get user details by ID.
2. PUT /users/{id}: Update user details by ID.
### **Amazon S3 File Management**
1. POST /files/upload: Upload a file to S3 (accepts file in the body).
2. GET /files/download/{fileName}: Download a file from S3.
3. DELETE /files/delete/{fileName}: Delete a file from S3.
4. GET /files/links/{fileName}: Get a usable link for a file stored on S3.