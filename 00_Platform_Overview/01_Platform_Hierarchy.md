# Platform Hierarchy

## Corporate Structure

ZANOVA (Company)
│
└── AI POWERED FLEET MANAGEMENT SYSTEM (AIFMS - Core Platform)
     │
     ├── Intelligence Engine (AI Core)
     │   ├── Predictive Analytics
     │   ├── Anomaly Detection
     │   ├── Optimization Algorithms
     │   ├── Safety Intelligence
     │   └── Fleet Health Monitoring
     │
     ├── Fleet Operating System (Software Layer)
     │   ├── Identity & Access Management
     │   ├── Fleet Orchestration
     │   ├── Payment Processing
     │   ├── Notification Engine
     │   └── Analytics & Reporting
     │
     ├── Smart Fleet Hub (IoT Edge Device)
     │   ├── Dashcam & Sensors
     │   ├── GPS & Offline Tracking
     │   ├── Edge AI Processing
     │   ├── WiFi Hotspot
     │   └── Emergency Communication
     │
     └── Data & Compliance Layer
         ├── Data Governance
         ├── Privacy & Security
         ├── Audit Logging
         ├── Regulatory Compliance
         └── Data Retention

          │
          ├── ZIFASE (Vertical: Passenger Taxi Ecosystem)
          ├── LOGIFLOW (Future: Logistics & Delivery Fleets)
          ├── GOVFLEET (Future: Government & Municipal Fleets)
          ├── MINEFLEET (Future: Mining Equipment & Transport)
          └── AGRIFLEET (Future: Agricultural Machinery Fleets)

## Layer Definitions

### Intelligence Engine
Central AI core that provides predictive analytics, anomaly detection, optimization algorithms, safety intelligence, and fleet health monitoring across all verticals.

### Fleet Operating System
Software layer providing identity management, fleet orchestration, payment processing, notification engine, and analytics reporting.

### Smart Fleet Hub
IoT edge device providing dashcam, GPS tracking, offline data logging, edge AI processing, WiFi hotspot, and emergency communication capabilities.

### Data & Compliance Layer
Governance framework for data privacy, security, audit logging, regulatory compliance, and data retention policies.

### Vertical Deployments
Industry-specific implementations built on the core platform:
- ZIFASE: Minibus taxi ecosystem (current)
- LOGIFLOW: Logistics and delivery fleets (future)
- GOVFLEET: Government and municipal fleets (future)
- MINEFLEET: Mining equipment and transport (future)
- AGRIFLEET: Agricultural machinery fleets (future)

## Separation Principle

The platform provides horizontal capabilities. Vertical implementations add industry-specific business logic, user interfaces, and regulatory compliance without modifying the core platform.