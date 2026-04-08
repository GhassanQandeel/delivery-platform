# 🚀 Local On-Demand Delivery Platform

A subscription-based local delivery platform that connects customers, local stores, and independent drivers in one comprehensive system. Inspired by global solutions like Uber Eats and Instacart, but designed specifically for regional needs with support for cash payments, map-based locations, and motorbike delivery.

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Technology Stack](#technology-stack)
- [Microservices](#microservices)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Deployment](#deployment)
- [Roadmap](#roadmap)
- [Contributing](#contributing)

## 🎯 Overview

This platform is a **multi-sided marketplace system** that enables:

- **Customers** to order products from nearby stores with live tracking
- **Stores** to sell and manage orders digitally without technical skills
- **Drivers** to earn flexible income by delivering orders

All in real-time, using mobile applications and a central backend system.

### Project Goals

1. **💼 Economic Empowerment**
   - Create job opportunities for drivers (especially youth)
   - Enable flexible income generation (part-time or full-time)

2. **🏪 Support Local Businesses**
   - Help small shops go digital
   - Increase sales without complex technology requirements

3. **🚀 Improve Daily Life**
   - Make ordering groceries and goods fast and easy
   - Reduce travel time and waiting in stores

4. **🌍 Local Innovation**
   - Cash payment support
   - Map-based location services
   - Optimized for motorbike delivery

## ✨ Key Features

### For Customers 👤
- Browse nearby stores and products
- Easy ordering with real-time tracking
- Flexible payment options (cash/future digital payments)
- Rate and review stores and drivers

### For Store Owners 🏪
- Digital storefront with no technical skills required
- Product catalog management (CRUD operations)
- Order management system
- Increased visibility and customer reach
- Sales tracking and analytics

### For Drivers 🚴
- Flexible work schedule
- Earnings per delivery
- Independent contractor model
- Real-time order notifications
- Navigation assistance

### For Admins 🛠
- User management
- System monitoring
- Report and issue handling
- Platform analytics

## 🏗 System Architecture

The platform follows a **microservices-based architecture** with the following components:

```
┌─────────────────────────────────────────────────────────┐
│                     API Gateway                          │
│          (Authentication, Routing, Security)             │
└─────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
┌───────▼────────┐  ┌──────▼──────┐   ┌───────▼────────┐
│  Auth Service  │  │User Service │   │ Store Service  │
│   (JWT Auth)   │  │  (Profiles) │   │   (Products)   │
└────────────────┘  └─────────────┘   └────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
┌───────▼────────┐  ┌──────▼──────┐   ┌───────▼────────┐
│ Order Service  │  │  Delivery   │   │  Subscription  │
│  (Lifecycle)   │  │   Service   │   │    Service     │
└────────────────┘  └─────────────┘   └────────────────┘
        │                   │                   │
        └───────────────────┼───────────────────┘
                            │
                    ┌───────▼────────┐
                    │ Message Broker │
                    │  (RabbitMQ)    │
                    └────────────────┘
```

### Architecture Principles
- **Microservices-based** for scalability and maintainability
- **Event-driven communication** via message broker
- **Loose coupling** between services
- **Database per service** for data isolation
- **API Gateway pattern** for centralized access control

## 🛠 Technology Stack

### Backend
- **Language**: Java
- **Framework**: Spring Boot
- **Cloud**: Spring Cloud (optional for scaling)
- **API Gateway**: Spring Cloud Gateway / NGINX
- **Authentication**: JWT (JSON Web Tokens)

### Mobile
- **Platform**: Android
- **Languages**: Java / Kotlin

### Frontend (Optional Web)
- **Framework**: React.js / Angular

### Database
- **RDBMS**: PostgreSQL
- **Pattern**: One database per microservice
  - `auth_db`
  - `user_db`
  - `order_db`
  - `store_db`
  - `subscription_db`
  - `delivery_db`
  - `rating_db`

### Messaging
- **MVP**: RabbitMQ
- **Future**: Apache Kafka (for high-scale)

### DevOps & Infrastructure
- **Containerization**: Docker
- **Orchestration**: 
  - Docker Compose (MVP)
  - Kubernetes (future scaling)
- **Notifications**: Firebase Cloud Messaging (FCM)
- **Maps**: Google Maps API
- **Deployment**: 
  - VPS: DigitalOcean / Hetzner (start)
  - Cloud: AWS / Google Cloud (scaling)

### Security
- JWT authentication
- HTTPS/SSL (Let's Encrypt)
- Role-based access control (RBAC)

### Monitoring & Logging
- **Basic**: Docker logs
- **Advanced** (future):
  - Prometheus (monitoring)
  - Grafana (visualization)

## 🔧 Microservices

### 1. Auth Service 🔐
- User authentication (login/register)
- JWT token generation and validation
- Role management (Customer, Store, Driver, Admin)

### 2. User Service 👥
- Manages all user types
- Profile management
- User data CRUD operations

### 3. Store Service 🏪
- Store registration and management
- Product catalog (CRUD)
- Store order handling
- Inventory management

### 4. Order Service 📦
- Order creation and management
- Order status lifecycle
- Central business logic for orders
- Order history

### 5. Delivery Service 🚴
- Driver availability tracking
- Order assignment to drivers
- Real-time delivery tracking
- Route optimization

### 6. Subscription Service 💳
- Manage subscriptions for stores and drivers
- Subscription plans and pricing
- Payment processing
- Expiration handling

### 7. Rating Service ⭐
- Store and driver ratings
- Reviews management
- Visibility scoring logic
- Feedback system

## 🚀 Getting Started

### Prerequisites
- Java 17+
- Docker & Docker Compose
- PostgreSQL 14+
- RabbitMQ
- Android Studio (for mobile development)
- Node.js 18+ (for web frontend, if applicable)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/delivery-platform.git
cd delivery-platform
```

2. **Set up environment variables**
```bash
cp .env.example .env
# Edit .env with your configuration
```

3. **Start services using Docker Compose**
```bash
docker-compose up -d
```

4. **Initialize databases**
```bash
./scripts/init-databases.sh
```

5. **Access the services**
- API Gateway: `http://localhost:8080`
- Admin Panel: `http://localhost:3000`
- RabbitMQ Management: `http://localhost:15672`

### Mobile App Setup

1. **Open Android project**
```bash
cd mobile-app
```

2. **Configure API endpoint**
```kotlin
// In app/src/main/java/config/ApiConfig.kt
const val BASE_URL = "http://your-api-gateway-url:8080"
```

3. **Build and run**
```bash
./gradlew build
./gradlew installDebug
```

## 📁 Project Structure

```
delivery-platform/
├── api-gateway/           # API Gateway service
├── auth-service/          # Authentication microservice
├── user-service/          # User management microservice
├── store-service/         # Store management microservice
├── order-service/         # Order processing microservice
├── delivery-service/      # Delivery tracking microservice
├── subscription-service/  # Subscription management microservice
├── rating-service/        # Rating and review microservice
├── mobile-app/           # Android mobile application
│   ├── customer-app/     # Customer application
│   ├── driver-app/       # Driver application
│   └── store-app/        # Store owner application
├── web-frontend/         # Optional web frontend
├── admin-panel/          # Administrative dashboard
├── docker-compose.yml    # Docker composition file
├── scripts/              # Utility scripts
└── docs/                 # Documentation
```

## 🌐 Deployment

### Phase 1: MVP (Single VPS)
```bash
# Deploy to VPS using Docker Compose
docker-compose -f docker-compose.prod.yml up -d
```

**Infrastructure:**
- Single VPS (DigitalOcean/Hetzner)
- All services containerized
- NGINX reverse proxy
- SSL via Let's Encrypt

### Phase 2: Scaling
```bash
# Deploy to Kubernetes cluster
kubectl apply -f k8s/
```

**Infrastructure:**
- Multiple servers
- Kubernetes cluster
- Load balancing
- Auto-scaling
- Multi-region support

### Domain Configuration
- Main domain: `yourapp.com`
- API: `api.yourapp.com`
- Admin: `admin.yourapp.com`

## 🗺 Roadmap

### Current (MVP)
- [x] Core microservices architecture
- [x] Basic authentication and authorization
- [x] Order management system
- [x] Store and product catalog
- [x] Driver assignment
- [x] Real-time tracking
- [x] Cash payment support

### Phase 2
- [ ] Digital payment integration
- [ ] Wallet system
- [ ] Advanced analytics dashboard
- [ ] Push notifications
- [ ] In-app chat support

### Phase 3
- [ ] AI-based driver assignment
- [ ] Predictive analytics
- [ ] Multi-city expansion
- [ ] Premium subscription tiers
- [ ] Loyalty program

### Long-term Vision
- Expand to multiple cities
- Build strong logistics network
- Become leading local delivery platform in the region

## 💰 Business Model

The platform generates revenue through:

1. **Subscription fees** from stores and drivers
2. **Delivery fees** per order
3. **Premium services** (future)
   - Featured store listings
   - Priority delivery
   - Advanced analytics

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow Java/Kotlin coding standards
- Write unit tests for new features
- Update documentation as needed
- Use meaningful commit messages


