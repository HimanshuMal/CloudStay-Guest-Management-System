# CloudStay Guest Management System

![Screenshot 2025-02-04 150351](https://github.com/user-attachments/assets/c4413f12-314b-4740-8eaa-e9ed5a8a2011)
![Screenshot 2025-02-04 150428](https://github.com/user-attachments/assets/bcc77fe5-4606-4732-adc7-f3275fc4e21f)

# Overview

CloudStay Guest Management System is a robust, cloud-based application designed for hotels to manage guest information efficiently. It leverages Python, Terraform, and AWS services such as S3 and RDS to ensure secure and scalable data storage, seamless access to guest records, and operational efficiency.

# Features

Guest Data Management: Store and retrieve guest details securely using Amazon RDS.

COVID-19 Test Management: Upload, manage, and access guest COVID-19 test PDFs via AWS S3.

Scalable Infrastructure: Infrastructure as Code (IaC) using Terraform for easy deployment and scalability.

# Table of Contents

Technologies Used

Setup and Installation

System Architecture

Usage

Terraform Configuration

Contributing

# Technologies Used

Programming Language: Python (Django for backend services)

Cloud Provider: AWS

S3: For storing and retrieving guest-related documents (e.g., COVID-19 test PDFs)

RDS: For secure and scalable relational database storage

Infrastructure as Code (IaC): Terraform

# Setup and Installation

Prerequisites

Python 3.8+

AWS CLI configured with appropriate permissions for S3 and RDS

Terraform 1.0+

PostgreSQL (for local testing if needed)

Step 1: Clone the Repository
git clone https://github.com/your-repo/cloudstay-guest-management.git
cd cloudstay-guest-management

Step 2: Install Dependencies
pip install -r requirements.txt

Step 3: Configure AWS and Terraform
AWS: Set up your AWS credentials using aws configure.
Terraform: Initialize Terraform in the terraform/ directory.

cd terraform
terraform init

Step 4: Deploy Infrastructure
Run the following commands in the terraform/ directory to deploy the necessary AWS resources:

terraform plan
terraform apply

Step 5: Configure Environment Variables
Create a .env file in the root directory with the following variables:

AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
AWS_REGION=your-region
DATABASE_URL=your-database-url
S3_BUCKET_NAME=your-s3-bucket

Step 6: Run the Application
Start the server:

python app.py
The application should now be accessible at http://localhost:5000.

# System Architecture

Core Components

Backend:

Built using Python with Django or Flask.

Handles API requests for guest management and document upload/download.

AWS S3:

Stores guest-related documents securely.

Provides signed URLs for secure access to files.

AWS RDS:

Relational database for managing guest data.

Optimized for secure, high-availability storage.

# Usage

API Endpoints

1. Guest Management

Create Guest
POST /api/guests

Payload:
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "phone": "1234567890"
}

Get Guest
GET /api/guests/{id}

2. Document Management

Upload COVID-19 Test PDF
POST /api/documents

Payload:
File (multipart/form-data)

Retrieve Document
GET /api/documents/{id}

# Terraform Configuration

The terraform/ directory contains configurations for AWS resource provisioning:

S3 Bucket

RDS Instance

Key Files

main.tf: Contains the main configuration for AWS resources.

variables.tf: Defines variables for dynamic resource creation.

outputs.tf: Specifies outputs such as RDS endpoint and S3 bucket name.

To destroy the infrastructure:
terraform destroy

# Contributing

Fork the repository.

Create a feature branch (git checkout -b feature-name).

Commit your changes (git commit -m 'Add new feature').

Push to the branch (git push origin feature-name).

Open a Pull Request.
