# AWS RDS Database Management Project

## Project Overview

This repository is part of a larger project and focuses exclusively on the **database** management using **AWS RDS (PostgreSQL)**. The database is containerized using **Docker**, and the project is designed to ensure secure, scalable, and efficient database management in the cloud. Key features include **data encryption at rest**, automated **backup and recovery** strategies, and integration with a broader AWS architecture.

The other components of the project—such as **Lambda functions**, **API Gateway**, and **ECR**—will be managed in a separate repository, with the frontend created using **AWS Honeycode**. The overall goal is to test **AWS deployment** and build a **serverless cloud structure**.

## Key Features

- **AWS RDS (PostgreSQL)**: Used for managing relational data with high availability, automated backups, and encryption at rest.
- **Docker Containerization**: Ensures consistent environment setup for database management and testing.
- **Data Encryption at Rest**: All data stored in AWS RDS is encrypted using AWS KMS to ensure security.
- **Backup and Recovery**: Automated backup configuration and point-in-time recovery to prevent data loss.

## Repository Contents

This repository contains the following key files:

1. **init-db/init.sql**: SQL script to initialize the database with tables (`users`, `products`, `purchases`) and sample data.
2. **app.py**: Python script to establish a connection to the RDS instance and run the SQL script for database initialization.
3. **Dockerfile**: Defines the containerized environment using Python 3.11, and installs necessary dependencies.
4. **docker-compose.yml**: Sets up the containerized services for the project, including environment variables for database connection.
5. **.env**: A file (not included in this repo for security reasons) that contains environment variables like database host, port, username, and password.

## Getting Started

### Prerequisites

- AWS RDS instance for PostgreSQL, set up with **data encryption at rest** and **automated backups**.
- Docker and Docker Compose installed on your local machine.
- PostgreSQL client (pgAdmin, psql) for testing.

### Setup Steps

1. **Create AWS RDS Instance**:

   - Set up a PostgreSQL RDS instance via the AWS Management Console.
   - Ensure the instance is in a private VPC and has encryption at rest enabled.
   - Configure automated backups and point-in-time recovery.

2. **Configure Environment Variables**:

   - Create a `.env` file at root.

3. **Run the Application**:

   - Build and run the Docker containers using Docker Compose:

     ```bash
     docker-compose up --build
     ```

   - This will set up a Python container that connects to the RDS instance and initializes the database with the SQL scripts.

4. **Verify Database Setup**:
   - Use a PostgreSQL client to verify that the `users`, `products`, and `purchases` tables have been created in your RDS instance.
   - Sample data should also be present in these tables, as defined in `init.sql`.

## Security and Best Practices

- **Encryption at Rest**: AWS KMS is used to ensure that all data stored in RDS is encrypted.
- **IAM Roles**: Use least-privilege IAM roles to restrict access to the RDS instance.
- **Backup and Recovery**: Automated backups and point-in-time recovery are enabled to safeguard against data loss.

## Future Enhancements

- **Infrastructure as Code (IAC)**: Future updates will integrate **Terraform** to automate the setup and scaling of the AWS infrastructure.
- **Separate Repositories**: A separate repository will manage the backend (Lambda functions), containerization (ECR), and API Gateway integration, along with frontend development using AWS Honeycode.

---

## Other Repositories

- **Backend and Frontend Integration**: Lambda functions, API Gateway, and ECR will be managed in another repository. This includes frontend development using **AWS Honeycode**.

---

## Technologies Used

- **AWS RDS (PostgreSQL)**: Relational database management.
- **Docker**: Containerization for local development.
- **psycopg2**: PostgreSQL adapter for Python to interact with the database.
