# Microservices Project

## Overview
This project is a **Spring Boot Microservices Architecture** implementation for an **E-commerce System**, which includes multiple microservices communicating via **REST, Kafka, and API Gateway**. The system will be containerized using **Docker** and deployed to **Google Cloud Run**. Additionally, it includes **Spring Cloud Config Server** for centralized configuration management and **Resilience4j Circuit Breaker** for fault tolerance.

## **Project Structure**
```
microservices-project/
│── api-gateway/ (Spring Cloud Gateway for routing requests)
│── config-server/ (Spring Cloud Config for centralized config management)
│── order-service/
│── product-service/
│── user-service/
│── recommendation-service/ (LLM-based AI service for recommendations)
│── kafka-event-service/ (Kafka-based event-driven service)
│── cloud-deployment/ (Cloud Run deployment scripts)
│── pom.xml (Parent POM for Microservices)
```

## **Key Features**
✅ **Spring Boot-based Microservices**
✅ **RESTful API communication**
✅ **API Gateway with Spring Cloud Gateway**
✅ **Centralized Configuration using Spring Cloud Config**
✅ **Circuit Breaker using Resilience4j**
✅ **Inter-Service Communication using Kafka**
✅ **Database Integration (PostgreSQL)**
✅ **AI-based Recommendations using OpenAI API**
✅ **Containerization with Docker**
✅ **Deployment on Google Cloud Run**

## **Microservices Details**

### 🟢 API Gateway (`api-gateway`)
- Central entry point for all microservices.
- Routes requests to appropriate services.
- Implements **Rate Limiting** and **Authentication**.

### 🟢 Config Server (`config-server`)
- Manages centralized configuration for all microservices.
- Uses a **Git-based** repository for storing configurations.

### 🟢 Order Service (`order-service`)
- Manages customer orders.
- Stores orders in PostgreSQL.
- Calls **Product Service** to check stock.
- Publishes **Kafka events** when an order is placed.
- Uses **Circuit Breaker (Resilience4j)** to handle failures.

### 🟢 Product Service (`product-service`)
- Manages product catalog.
- Provides product details to **Order Service**.
- Listens to **Kafka events** for stock updates.

### 🟢 User Service (`user-service`)
- Handles user authentication and profiles.
- Uses **Spring Security + JWT**.
- Provides authentication for all services.

### 🟢 AI-Powered Recommendation Service (`recommendation-service`)
- Fetches user order history.
- Calls **OpenAI API (GPT)** to generate product recommendations.
- Provides AI-based suggestions for users.

### 🟢 Kafka Event Service (`kafka-event-service`)
- Handles **event-driven communication**.
- Listens to **Order and Product Service events**.
- Ensures data consistency using **SAGA pattern**.

### 🟢 Deployment (`cloud-deployment`)
- **Docker Compose** for local testing.
- **Cloud Build + Cloud Run** for GCP deployment.
- **GitHub Actions for CI/CD**.

## **Technology Stack**
- **Java 17, Spring Boot 3.x**
- **Spring Cloud (Feign, Circuit Breaker, Config Server, Gateway)**
- **Kafka for Messaging**
- **PostgreSQL for Database**
- **OpenAI GPT API for AI integration**
- **Docker for Containerization**
- **Google Cloud Run for Deployment**

## **How to Run Locally**
```sh
docker-compose up -d
mvn clean install
mvn spring-boot:run -pl api-gateway
```

## **Deployment to Cloud Run**
```sh
gcloud builds submit --tag gcr.io/your-project-id/api-gateway
```

🚀 **Next Steps:** Implement Kafka event processing & AI-based recommendations! Let me know if you need enhancements! 😊
