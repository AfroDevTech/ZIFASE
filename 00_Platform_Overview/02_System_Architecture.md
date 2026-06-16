# System Architecture

## High-Level Architecture

+---------------------------------------------------------------------------------+
|                         VERTICAL APPLICATIONS                                   |
|                                                                                 |
|  +--------------+  +--------------+  +--------------+  +--------------+       |
|  |   ZIFASE     |  |  LOGIFLOW    |  |  GOVFLEET    |  |  MINEFLEET   |       |
|  |   (Taxi)     |  |  (Logistics) |  |  (Government)|  |  (Mining)    |       |
|  +------+-------+  +------+-------+  +------+-------+  +------+-------+       |
|         |                 |                 |                 |                |
|         +-----------------+-----------------+-----------------+                |
|                                    |                                            |
|         +--------------------------+--------------------------+                |
|         |                          |                          |                |
|         v                          v                          v                |
|  +--------------+          +--------------+          +--------------+         |
|  |  Fleet       |          |  Intelligence|          |  Smart Fleet |         |
|  |  Operating   |----------|    Engine    |----------|    Hub       |         |
|  |  System      |          |   (AI Core)  |          |   (IoT)      |         |
|  +--------------+          +--------------+          +--------------+         |
|         |                          |                          |                |
|         +--------------------------+--------------------------+                |
|                                    |                                            |
|                           +--------+--------+                                  |
|                           |  Data &         |                                  |
|                           |  Compliance     |                                  |
|                           |  Layer          |                                  |
|                           +-----------------+                                  |
|                                                                                 |
+---------------------------------------------------------------------------------+
                                    |
                                    v
                    +-----------------------------+
                    |    ZANOVA CLOUD PLATFORM    |
                    |    (Infrastructure Layer)    |
                    +-----------------------------+

## Component Descriptions

### Fleet Operating System
Microservices-based backend providing:
- Identity and access management
- Fleet orchestration and vehicle management
- Booking and trip management
- Payment processing
- Notification delivery
- Analytics and reporting

### Intelligence Engine
AI/ML services providing:
- Predictive demand forecasting
- Predictive maintenance scheduling
- Driver safety scoring
- Collision detection
- Theft detection
- Route optimization
- Passenger clustering

### Smart Fleet Hub
Edge IoT device providing:
- Dashboard camera (2K/4K)
- Multi-band GNSS positioning
- Inertial measurement unit (6-axis)
- WiFi 6 hotspot
- Cellular connectivity (4G/5G)
- Offline data storage (128GB+)
- Edge AI processing
- Emergency communication

### Data & Compliance Layer
Governance services providing:
- Data classification and handling
- Privacy compliance (POPIA, GDPR)
- Audit trail generation
- Data retention management
- Regulatory reporting

## Data Flow

1. Smart Fleet Hub collects sensor, GPS, and video data
2. Edge AI processes data in real-time
3. Data transmitted to cloud via 4G/5G or offline cache
4. Fleet Operating System ingests and stores data
5. Intelligence Engine analyzes data for predictions
6. Insights delivered to vertical applications
7. Vertical applications present to end users

## Communication Protocols

| Component | Protocol | Purpose |
|-----------|----------|---------|
| Hub to Cloud | MQTT | Lightweight telemetry |
| Hub to Cloud | WebSocket | Real-time event streaming |
| Client to API | HTTPS/REST | CRUD operations |
| Client to API | WebSocket | Live updates |
| Service to Service | gRPC | Internal microservice communication |
| Service to Service | Pub/Sub | Event-driven messaging |