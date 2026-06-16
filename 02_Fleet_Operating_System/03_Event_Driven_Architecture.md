# Event-Driven Architecture

## Overview

The Fleet Operating System uses event-driven architecture to enable loose coupling, scalability, and real-time responsiveness across all platform components.

## Event Bus

Primary event bus: RabbitMQ / Google Pub/Sub

## Core Events

### Fleet Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| vehicle.registered | Vehicle Service | New vehicle added to platform |
| vehicle.updated | Vehicle Service | Vehicle metadata updated |
| vehicle.status.changed | Vehicle Service | Vehicle operational status changed |
| vehicle.maintenance.due | Maintenance Service | Scheduled maintenance required |
| vehicle.telemetry.received | IoT Ingest Service | New telemetry data point received |

### Trip Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| trip.created | Trip Service | New trip created |
| trip.started | Trip Service | Trip commenced |
| trip.updated | Trip Service | Trip status/position updated |
| trip.completed | Trip Service | Trip finished |
| trip.cancelled | Trip Service | Trip cancelled |

### Booking Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| booking.created | Booking Service | New booking initiated |
| booking.confirmed | Booking Service | Booking confirmed |
| booking.assigned | Booking Service | Driver assigned to booking |
| booking.cancelled | Booking Service | Booking cancelled |

### Payment Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| payment.initiated | Payment Service | Payment process started |
| payment.processed | Payment Service | Payment completed |
| payment.failed | Payment Service | Payment failed |
| payment.refunded | Payment Service | Payment refunded |

### Safety Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| incident.detected | Safety Service | Safety incident detected |
| incident.escalated | Safety Service | Incident escalated to stakeholders |
| incident.resolved | Safety Service | Incident resolved |
| collision.detected | IoT/Safety Service | Collision detected by hub |
| theft.detected | IoT/Safety Service | Theft/hijacking detected |

### Hub Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| hub.registered | IoT Service | Smart Fleet Hub registered |
| hub.connected | IoT Service | Hub connected to platform |
| hub.disconnected | IoT Service | Hub disconnected |
| hub.offline | IoT Service | Hub entered offline mode |
| hub.online | IoT Service | Hub returned online |
| hub.emergency | IoT Service | Emergency event from hub |
| hub.ota.available | IoT Service | OTA update available |

### AI Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| prediction.demand | AI Service | Demand forecast generated |
| prediction.maintenance | AI Service | Maintenance prediction generated |
| prediction.safety | AI Service | Safety risk prediction |
| alert.driver.safety | AI Service | Driver safety alert triggered |
| alert.fleet.health | AI Service | Fleet health alert triggered |

### Notification Events

| Event Name | Publisher | Description |
|------------|-----------|-------------|
| notification.pushed | Notification Service | Push notification delivered |
| notification.sms | Notification Service | SMS delivered |
| notification.email | Notification Service | Email delivered |

## Event Flow Example: Trip Creation

1. User creates booking via Passenger App
2. Booking Service publishes booking.created
3. Notification Service consumes: sends confirmation
4. AI Service consumes: updates demand forecast
5. Trip Service consumes: creates trip record
6. Trip Service publishes trip.created
7. Fleet Service consumes: updates vehicle availability
8. Driver Service consumes: notifies matching drivers
9. Real-Time Engine consumes: updates occupancy for all clients

## Event Flow Example: Emergency Detection

1. Smart Fleet Hub detects collision via IMU sensors
2. Hub publishes hub.emergency with collision data
3. Safety Service consumes: creates incident record
4. Safety Service publishes incident.detected
5. Notification Service consumes: sends alerts to:
   - Fleet owner
   - Association admin
   - Emergency contacts
   - Emergency services
6. Incident Service consumes: initiates escalation tree
7. Analytics Service consumes: logs event for trend analysis
8. Real-Time Engine consumes: updates incident dashboard for all stakeholders

## Event Flow Example: Offline Hub Reconnection

1. Smart Fleet Hub regains internet connectivity
2. Hub publishes hub.online
3. IoT Ingest Service consumes: syncs offline data
4. Trip Service consumes: updates trip status with cached data
5. Safety Service consumes: processes any pending emergency events
6. Notification Service consumes: notifies relevant parties of reconnection

## Event Schema

All events follow this structure:

{
  "event_id": "uuid",
  "event_type": "string",
  "event_version": "string",
  "timestamp": "ISO-8601",
  "source": "string",
  "correlation_id": "uuid",
  "payload": "object",
  "metadata": {
    "environment": "string",
    "trace_id": "string",
    "span_id": "string"
  }
}

## Event Retention

- Events retained for 30 days
- Critical events retained for 7 years (regulatory requirement)
- Event replay available for 48 hours
- Dead letter queue for failed events

## Error Handling

- Failed events retry with exponential backoff
- Max retries: 5
- Failed events routed to dead letter queue
- Dead letter queue monitored for alerts
- Manual intervention required for persistent failures