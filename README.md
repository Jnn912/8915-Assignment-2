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

## Updated Architecture
![Updated Architecture Diagram](architecture-diagram.png)

The updated architecture diagram includes:
- Replacement of RabbitMQ with Azure Service Bus for message queuing.
- Integration of an AI-Service for product description and image generation using GPT-4 and DALL-E.

## Application and Architecture Description
The application consists of the following components:

1. **Store-Front (Vue.js)**: Customer-facing interface to browse products and place orders.
2. **Store-Admin (Vue.js)**: Employee-facing interface for managing products and monitoring orders.
3. **Order-Service (Node.js)**: Handles order creation and sends data to Azure Service Bus.
4. **Product-Service (Rust)**: Manages product data (CRUD operations) and integrates with AI-Service for product descriptions and images.
5. **Makeline-Service (Go)**: Reads order messages from Azure Service Bus and processes them.
6. **AI-Service (Python)**: Utilizes GPT-4 for generating product descriptions and DALL-E for creating product images.
7. **MongoDB (Database)**: Stores orders and product data.

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

### Steps
1. Clone the repository:
   ```bash
   git clone <repository-link>
   cd best-buy-application
   ```

2. Build and push Docker images for each microservice:
   ```bash
   docker build -t <dockerhub-username>/store-front ./store-front
   docker push <dockerhub-username>/store-front
   # Repeat for other services
   ```

3. Deploy services to Kubernetes:
   ```bash
   kubectl apply -f deployment-files/
   ```

4. Verify all pods are running:
   ```bash
   kubectl get pods
   ```

5. Access the application:
   - Store-Front: `http://<external-ip>/`
   - Store-Admin: `http://<external-ip>/admin`

## Microservices Overview
| Microservice      | Description                                         | Repository Link                           |
|-------------------|-----------------------------------------------------|-------------------------------------------|
| Store-Front       | Customer-facing interface                          | [Store-Front Repo](#)                     |
| Store-Admin       | Employee-facing interface                          | [Store-Admin Repo](#)                     |
| Order-Service     | Handles order creation and integrates with Azure   | [Order-Service Repo](#)                   |
| Product-Service   | Manages product data and integrates with AI-Service| [Product-Service Repo](#)                 |
| Makeline-Service  | Processes orders from Azure Service Bus            | [Makeline-Service Repo](#)                |
| AI-Service        | Generates product descriptions and images          | [AI-Service Repo](#)                      |

## Docker Images
| Microservice      | Docker Image                                       | Docker Hub Link                           |
|-------------------|-----------------------------------------------------|-------------------------------------------|
| Store-Front       | `<dockerhub-username>/store-front`                 | [Link](#)                                 |
| Store-Admin       | `<dockerhub-username>/store-admin`                 | [Link](#)                                 |
| Order-Service     | `<dockerhub-username>/order-service`               | [Link](#)                                 |
| Product-Service   | `<dockerhub-username>/product-service`             | [Link](#)                                 |
| Makeline-Service  | `<dockerhub-username>/makeline-service`            | [Link](#)                                 |
| AI-Service        | `<dockerhub-username>/ai-service`                  | [Link](#)                                 |

## Limitations and Issues
- **Azure Service Bus Latency**: Initial integration testing shows slight delays under high traffic.
- **AI-Service Response Time**: GPT-4 and DALL-E API calls may experience latency during peak usage.
- **Scalability of MongoDB**: Requires monitoring and potential sharding for large datasets.

## Demo Video
[Watch the Demo Video Here](#)
