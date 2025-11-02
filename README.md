# Hello World Three-Tier Application

This repository contains a simple "Hello World" application built using a three-tier architecture. The application demonstrates the fundamental concepts of separating frontend, backend, and database components in a web application.

## Architecture Overview

![alt text](aws-three-tier-architecture.png)

The application follows the classic three-tier architecture:

1. **Frontend Tier (Presentation Layer)**
   - HTML/CSS/JavaScript
   - Served by NGINX web servers
   - Handles user interface and interactions

2. **Backend Tier (Application Layer)**
   - PHP API
   - Processes business logic
   - Communicates with database
   - Serves data to frontend

3. **Database Tier (Data Layer)**
   - MySQL database
   - Stores application data
   - Provides data persistence

## Features

- Display messages from the database
- Add new messages to the database
- Basic responsive design

## AWS Infrastructure Components

When deployed on AWS, the infrastructure includes:

- **Web ALB**: Load balancer for distributing traffic to web servers
- **NGINX Servers**: EC2 instances in an auto-scaling group
- **App ALB**: Load balancer for distributing traffic to application servers
- **PHP Servers**: EC2 instances in an auto-scaling group
- **RDS MySQL**: Managed relational database service


## Local Setup

### Prerequisites

- Web server with PHP support (XAMPP, WAMP, MAMP, etc.)
- MySQL database

### Steps

1. Create VPC
2. Create subnets
    1. Web Public 1a, 1b, 1c
    2. Web Private 1a, 1b, 1c
    3. App Private 1a, 1b, 1c
    4. Db Private 1a, 1b, 1c
3. Create route tables
    1. Web Public
    2. Web Private 1a, 1b, 1c
    3. App Private 1a, 1b, 1c
    4. Db Private 1a, 1b, 1c
4. Associate route tables with subnet
5. Create internet Gateway (IGW)
    1. Attach it to VPC
6. Create NAT gateway (NATGW) in web public subnet
7. Add IGW and NAT routes in route table
    1. Public -> IGW
    2. Private -> NAT
8. Create security groups
    1. Frontend ALB
    2. Frontend Servers
    3. Backend ALB
    4. Backend Servers
    5. Db Private Servers
9. Create database subnet group
10. Create database server
11. Create Frontend ALB
    1. Create Frontend ALB target group 
12. Create Backend ALB
    1. Create Backend ALB target group
13. Create Frontend Server AMI
    1. Install Nginx
    2. Install Git
14. Create Backend Server AMI
    1. Install PHP, MySQL, Apache
    2. Install Git
    3. Run the database script
15. Create the Launch Template for Frontend Server
16. Create the Launch Template for Backend Server
17. Create the Auto Scaling Group for Frontend Server
18. Create the Auto Scaling Group for Backend Server

## Development

### Frontend Development

The frontend is built with plain HTML, CSS, and JavaScript. It uses the Fetch API to communicate with the backend.

To make changes to the frontend:
1. Modify the HTML/CSS/JavaScript files in the `frontend` directory
2. Test the changes locally

### Backend Development

The PHP backend provides simple API endpoints for retrieving and saving messages.

To make changes to the backend:
1. Modify the PHP files in the `backend/api` directory
2. Test the changes locally

## Security Considerations

This is a demo application and lacks several security features that would be necessary in a production environment:

- Input validation and sanitization
- Authentication and authorization
- HTTPS encryption
- Protection against SQL injection (although PDO with prepared statements is used)
- CORS configuration

## Acknowledgements

This sample application was created as a demonstration of AWS three-tier architecture principles.
