# Best Buy Cloud-Native Application

CST_8915_Assignment2

## Application Overview
This is a cloud-native application developed for Best Buy's online store, based on microservices architecture. The application enables customers to browse products, place orders, and allows employees to manage products and process orders.

## Architecture
[架构图将在这里添加]

The application consists of the following components:

### Core Services
- **Store-Front**: Customer-facing web application for browsing and ordering products
- **Store-Admin**: Employee-facing web application for managing products and orders
- **Order-Service**: Handles order creation and integrates with Azure Service Bus
- **Product-Service**: Manages product information with CRUD operations
- **Makeline-Service**: Processes orders from the queue
- **AI-Service**: Generates product descriptions and images using GPT-4 and DALL-E
- **Database**: MongoDB for data persistence
- **Azure Service Bus**: Managed service for order queue management

### Service Repositories
| Service | Repository Link |
|---------|----------------|
| Store-Front | [Link to be added] |
| Store-Admin | [Link to be added] |
| Order-Service | [Link to be added] |
| Product-Service | [Link to be added] |
| Makeline-Service | [Link to be added] |
| AI-Service | [Link to be added] |

### Docker Images
| Service | Docker Image Link |
|---------|------------------|
| Store-Front | [Link to be added] |
| Store-Admin | [Link to be added] |
| Order-Service | [Link to be added] |
| Product-Service | [Link to be added] |
| Makeline-Service | [Link to be added] |
| AI-Service | [Link to be added] |

## Deployment Instructions
[Deployment instructions will be added here]

## Demo Video
[Video link will be added here]
