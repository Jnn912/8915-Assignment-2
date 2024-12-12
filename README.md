# Best Buy Cloud-Native Application

## CST_8915_Assignment2

## Application Overview
This is a cloud-native application developed for Best Buy's online store, based on microservices architecture. The application enables customers to browse products, place orders, and allows employees to manage products and process orders. Following the design principles of the Algonquin Pet Store (On Steroids), this implementation replaces RabbitMQ with Azure Service Bus as a managed backing service and incorporates AI capabilities for enhanced product descriptions and image generation.

## Architecture
![Architecture Diagram](./images/architecture.png)

### Architecture Explanation
The application follows a microservices architecture pattern where each service is independently deployable and scalable. The key enhancement from the original Algonquin Pet Store design is the replacement of RabbitMQ with Azure Service Bus for more robust and managed message queue handling.

### Core Services
* **Store-Front**: Customer-facing web application for browsing and ordering products (Vue.js)
* **Store-Admin**: Employee-facing web application for managing products and orders (Vue.js)
* **Order-Service**: Handles order creation and integrates with Azure Service Bus (Node.js)
* **Product-Service**: Manages product information with CRUD operations (Rust)
* **Makeline-Service**: Processes orders from the queue (Go)
* **AI-Service**: Generates product descriptions and images using GPT-4 and DALL-E (Python)
* **Database**: MongoDB for data persistence
* **Azure Service Bus**: Managed service for order queue management

### Service Repositories
| Service | Repository Link |
|---------|----------------|
| Store-Front | [store-front-repo](https://github.com/YourUsername/store-front) |
| Store-Admin | [store-admin-repo](https://github.com/YourUsername/store-admin) |
| Order-Service | [order-service-repo](https://github.com/YourUsername/order-service) |
| Product-Service | [product-service-repo](https://github.com/YourUsername/product-service) |
| Makeline-Service | [makeline-service-repo](https://github.com/YourUsername/makeline-service) |
| AI-Service | [ai-service-repo](https://github.com/YourUsername/ai-service) |

### Docker Images
| Service | Docker Image Link |
|---------|------------------|
| Store-Front | [store-front-image](https://hub.docker.com/r/yourusername/store-front) |
| Store-Admin | [store-admin-image](https://hub.docker.com/r/yourusername/store-admin) |
| Order-Service | [order-service-image](https://hub.docker.com/r/yourusername/order-service) |
| Product-Service | [product-service-image](https://hub.docker.com/r/yourusername/product-service) |
| Makeline-Service | [makeline-service-image](https://hub.docker.com/r/yourusername/makeline-service) |
| AI-Service | [ai-service-image](https://hub.docker.com/r/yourusername/ai-service) |

## Deployment Instructions

### Prerequisites
- Azure Kubernetes Service (AKS) cluster
- Azure CLI installed and configured
- kubectl installed and configured
- Docker installed
- Access to Azure Service Bus
- OpenAI API access (for GPT-4 and DALL-E integration)

### Deployment Steps

1. Clone the Repository
```bash
git clone https://github.com/YourUsername/24F_LabAssignment2.git
cd 24F_LabAssignment2

# Create Azure Service Bus namespace
az servicebus namespace create \
    --name bestbuy-servicebus \
    --resource-group myResourceGroup \
    --location eastus

# Create queue for orders
az servicebus queue create \
    --name orders \
    --namespace-name bestbuy-servicebus \
    --resource-group myResourceGroup

# Deploy MongoDB StatefulSet
kubectl apply -f Deployment-Files/mongodb-statefulset.yaml

# Verify MongoDB deployment
kubectl get statefulset
kubectl get pvc

# Deploy all microservices
kubectl apply -f Deployment-Files/store-front-deployment.yaml
kubectl apply -f Deployment-Files/store-admin-deployment.yaml
kubectl apply -f Deployment-Files/order-service-deployment.yaml
kubectl apply -f Deployment-Files/product-service-deployment.yaml
kubectl apply -f Deployment-Files/makeline-service-deployment.yaml
kubectl apply -f Deployment-Files/ai-service-deployment.yaml

# Verify deployments
kubectl get deployments
kubectl get pods
kubectl get services

# Create secret for OpenAI API key
kubectl create secret generic openai-secret \
    --from-literal=api-key=your-api-key

# Verify AI service configuration
kubectl get secrets

# Get service endpoints
kubectl get services

# Test application health
kubectl get pods
kubectl logs <pod-name>

## Demo Video
[Demo Video Link](https://youtu.be/your-video-id)

### Video Contents (5 minutes)
1. Application Architecture Overview (1 minute)
   - Explanation of microservices architecture
   - Highlight Azure Service Bus integration
   - Overview of AI service integration

2. Deployment Demonstration (2 minutes)
   - Kubernetes deployment process
   - Service configuration
   - Verification of running services

3. Application Features (2 minutes)
   - Store-Front functionality
     * Product browsing
     * Order placement
   - Store-Admin functionality
     * Product management
     * Order processing
   - AI Features Demonstration
     * GPT-4 generated product descriptions
     * DALL-E generated product images
   - Azure Service Bus Integration
     * Order queue management
     * Message processing

Note: The complete source code and deployment files can be found in this repository.
