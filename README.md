# Microservices Project

## Overview
This project is a **Spring Boot Microservices Architecture** implementation for an **E-commerce System**, which includes multiple microservices communicating via **REST and Kafka**. The system will be containerized using **Docker** and deployed to **Google Cloud Run**.

## **Project Structure**
```
microservices-project/
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
✅ **Database Integration (PostgreSQL)**
✅ **Inter-Service Communication using Kafka**
✅ **Circuit Breaker using Resilience4j**
✅ **AI-based Recommendations using OpenAI API**
✅ **Containerization with Docker**
✅ **Deployment on Google Cloud Run**

## **Microservices Details**

### 🟢 Order Service (`order-service`)
- Manages customer orders.
- Stores orders in PostgreSQL.
- Calls **Product Service** to check stock.
- Publishes **Kafka events** when an order is placed.

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
- **Java 11, Spring Boot 2.7.x**
- **Spring Cloud (Feign, Circuit Breaker, Config Server)**
- **Kafka for Messaging**
- **PostgreSQL for Database**
- **OpenAI GPT API for AI integration**
- **Docker for Containerization**
- **Google Cloud Run for Deployment**

## **How to Run Locally**
```sh
docker-compose up -d
mvn clean install
mvn spring-boot:run -pl order-service
```

## **Deployment to Cloud Run**
```sh
gcloud builds submit --tag gcr.io/your-project-id/order-service
```

🚀 **Next Steps:** Implement Kafka event processing & AI-based recommendations! Let me know if you need enhancements! 😊

