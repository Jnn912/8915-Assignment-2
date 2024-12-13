# Best Buy Cloud-Native Application

## Table of Contents
- [Overview](#overview)
- [Updated Architecture](#updated-architecture)
- [Application and Architecture Description](#application-and-architecture-description)
- [Deployment Instructions](#deployment-instructions)
- [Microservices Overview](#microservices-overview)
- [Docker Images](#docker-images)
- [Limitations and Issues](#limitations-and-issues)
- [Demo Video](#demo-video)

---

## Overview
The Best Buy Cloud-Native Application is a scalable, microservice-based solution designed for e-commerce. This project is inspired by the Algonquin Pet Store architecture and aims to demonstrate proficiency in modern cloud-native technologies, including containerization, Kubernetes orchestration, and AI integration.

### Key Objectives:
1. **Customer Interface**: Enable customers to browse products, view AI-generated descriptions, and place orders seamlessly.
2. **Employee Management**: Provide an intuitive admin interface for employees to manage products and monitor orders.
3. **AI Integration**: Use GPT-4 to generate dynamic product descriptions and DALL-E for creating product images.
4. **Cloud Scalability**: Deploy all services on Kubernetes with Azure Service Bus as the message broker.

### Technologies Used:
- **Frontend**: Vue.js
- **Backend**: Node.js, Rust, Go, Python
- **Message Queue**: Azure Service Bus
- **Database**: MongoDB
- **AI Models**: GPT-4 and DALL-E
- **Orchestration**: Kubernetes

##  Architecture
<img width="744" alt="architecture-diagram" src="https://github.com/user-attachments/assets/51e021fa-e50d-47f4-8820-b11f96a487b9" />


### Key Components:
1. **Store-Front (Vue.js)**: Customer-facing interface for browsing products and placing orders.
2. **Store-Admin (Vue.js)**: Employee-facing interface for managing products and monitoring orders.
3. **Order-Service (Node.js)**: Processes customer orders and sends them to Azure Service Bus for asynchronous communication.
4. **Product-Service (Rust)**: Handles product CRUD operations and integrates with AI-Service for dynamic descriptions and images.
5. **Makeline-Service (Go)**: Listens to Azure Service Bus for order messages and processes them, updating MongoDB.
6. **AI-Service (Python)**: Provides REST APIs to generate product descriptions using GPT-4 and images using DALL-E.
7. **MongoDB**: A NoSQL database used for persisting product and order data.
8. **Azure Service Bus**: A managed message broker for decoupling services and enabling scalability.

### Component Interactions:
- **Customer Actions**: Customers interact with Store-Front to view products (via Product-Service) and place orders (via Order-Service).
- **Employee Actions**: Employees use Store-Admin to manage products and monitor the status of orders.
- **Order Workflow**:
   1. Order-Service sends order data to Azure Service Bus.
   2. Makeline-Service reads order messages, processes them, and updates MongoDB.
- **AI Integration**: Product-Service makes HTTP requests to AI-Service for generating dynamic content.


## Deployment Instructions
### Prerequisites
1. **Tools**:
   - Kubernetes Cluster (e.g., AKS, Minikube)
   - Docker
   - Azure CLI
   - kubectl

2. **Environment Setup**:
   - Ensure Azure Service Bus and MongoDB are configured.
   - Create the necessary Azure resources using Azure CLI.


## Microservices Overview
| Microservice      |                                   | Repository Link                           |
|-------------------|-----------------------------------------------------|-------------------------------------------|
| Store-Front       |     | [Store-Front Repo](https://github.com/Jnn912/store-front-L8)       |
| Store-Admin       |     | [Store-Admin Repo](https://github.com/Jnn912/store-admin-L8)       |
| Order-Service     |     | [Order-Service Repo](https://github.com/Jnn912/order-service-L8)   |
| Product-Service   |     | [Product-Service Repo](https://github.com/Jnn912/product-service-L8)|
| Makeline-Service  |     | [Makeline-Service Repo](https://github.com/Jnn912/makeline-service-L8) |
| AI-Service        |     | [AI-Service Repo](https://github.com/Jnn912/ai-service-L8)|
| virtual-worker    |     | [[virtual-worker Repo](https://github.com/Jnn912/virtual-worker-L8)|
| virtual-customer  |     | [[virtual-customer Repo](https://github.com/Jnn912/virtual-customer-L8)|

## Docker Images
| Microservice      |                                        | Docker Hub Link                           |
|-------------------|-----------------------------------------------------|-------------------------------------------|
| Store-Front       |            | [https://hub.docker.com/r/xijin324/store-front/tags](#)                                 |
| Store-Admin       |            | [https://hub.docker.com/r/xijin324/store-admin/tags](#)                                 |
| Order-Service     |            | [https://hub.docker.com/r/xijin324/order-service/tags](#)                                 |
| Product-Service   |            | [https://hub.docker.com/r/xijin324/product-service/tags](#)                                 |
| Makeline-Service  |            | [https://hub.docker.com/r/xijin324/makeline-service/tags](#)                                 |
| AI-Service        |            | [https://hub.docker.com/r/xijin324/ai-service/tags](#)                                 
| virtual-customer  |            | https://hub.docker.com/r/xijin324/virtual-customer/tags/ai-service/tags                              
| virtual-worker    |            | https://hub.docker.com/r/xijin324/virtual-worker/tags       

## Limitations and Issues
- **Azure Service Bus Latency**: Initial integration testing shows slight delays under high traffic.
- **AI-Service Response Time**: GPT-4 and DALL-E API calls may experience latency during peak usage.
- **Scalability of MongoDB**: Requires monitoring and potential sharding for large datasets.

## Demo Video
[Watch the Demo Video Here](#)
