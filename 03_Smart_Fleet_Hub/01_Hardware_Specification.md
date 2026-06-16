# Smart Fleet Hub - Hardware Specification

## Overview

The Smart Fleet Hub is the primary IoT edge device in the platform. It provides data collection, edge processing, connectivity, and emergency communication capabilities.

## Hardware Components

### Processing Unit

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Processor | ARM Cortex-A72 (quad-core) | Main application processing |
| NPU | 4 TOPS neural processing unit | Edge AI acceleration |
| RAM | 8GB LPDDR4 | Application memory |
| Storage | 128GB eMMC / microSD | Operating system and data |
| RTC | Integrated real-time clock | Timestamp synchronization |

### Camera System

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Resolution | 2K (2560 x 1440) or 4K | Video recording |
| Field of View | 140 degrees | Wide road view |
| Night Vision | Infrared LED array | Low-light recording |
| Frame Rate | 30 fps | Smooth video capture |
| Lens | Glass, anti-glare coating | Optical clarity |

### Positioning System

| Component | Specification | Purpose |
|-----------|---------------|---------|
| GNSS | Multi-band GPS, GLONASS, Galileo | Accurate positioning |
| Accuracy | 1.5m (open sky) | Location precision |
| Update Rate | 10 Hz | Real-time tracking |
| Hot Start | 1 second | Quick acquisition |
| Cold Start | 25 seconds | Initial acquisition |

### Inertial Measurement Unit

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Accelerometer | +/- 16g range | Collision detection |
| Gyroscope | +/- 2000 dps | Orientation tracking |
| Magnetometer | +/- 49 gauss | Heading reference |
| Sample Rate | 1000 Hz | High-frequency data |
| Resolution | 16-bit | Data precision |

### Connectivity

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Cellular | 4G LTE Cat 6 / 5G NR | Cloud communication |
| SIM | eSIM with carrier switching | Network resilience |
| WiFi | 802.11ax (WiFi 6) | In-vehicle hotspot |
| Bluetooth | 5.2 LE | Peripheral connectivity |
| Ethernet | 100/1000 Base-T | Wired diagnostics |
| Antenna | Dual-band MIMO | Signal reliability |

### Power System

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Input Voltage | 12-24V DC | Vehicle power compatibility |
| Power Consumption | 10W typical | Energy efficiency |
| Backup Battery | 2500mAh LiFePO4 | 30-60 minute runtime |
| Charging | 2A fast charge | Quick recovery |
| Protection | Over-voltage, reverse polarity | Device protection |

### Environmental Specifications

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Operating Temperature | -20C to 70C | Vehicle environment |
| Storage Temperature | -30C to 85C | Storage tolerance |
| Ingress Protection | IP65 | Dust and water resistance |
| Vibration Resistance | MIL-STD-810G | Vehicle vibration tolerance |
| Shock Resistance | 50G | Impact protection |

### Interfaces

| Component | Specification | Purpose |
|-----------|---------------|---------|
| USB-C | USB 3.0 | Debug and diagnostics |
| Micro-HDMI | 1080p output | Video playback |
| 3.5mm Audio | Stereo | Speaker/microphone |
| CAN Bus | CAN 2.0B | Vehicle OBD-II integration |
| GPIO | 8-pin header | External sensors |

## Physical Dimensions

| Parameter | Measurement |
|-----------|-------------|
| Width | 100mm |
| Height | 60mm |
| Depth | 30mm |
| Weight | 250g |
| Mounting | Adhesive bracket / suction cup |

## Regulatory Compliance

| Standard | Requirement |
|----------|-------------|
| FCC | Part 15 Class B |
| CE | EN 55032, EN 55035 |
| IC | RSS-247 |
| RoHS | EU Directive 2011/65/EU |
| REACH | EU Regulation 1907/2006 |
| E-Mark | UN ECE R10 |

## Power States

| State | Power Draw | Description |
|-------|------------|-------------|
| Active | 10W | Full operation |
| Idle | 5W | Standby, GPS active |
| Sleep | 1W | Low-power mode |
| Off | 0W | Powered down |

## Communication Protocol

### MQTT Topics

| Topic | Direction | Purpose |
|-------|-----------|---------|
| /hub/{hub_id}/telemetry | Publish | Telemetry data |
| /hub/{hub_id}/event | Publish | Event notification |
| /hub/{hub_id}/command | Subscribe | Platform commands |
| /hub/{hub_id}/emergency | Publish | Emergency event |
| /hub/{hub_id}/status | Publish | Heartbeat status |
| /hub/{hub_id}/ota | Subscribe/Response | OTA update management |
| /hub/{hub_id}/sync | Publish | Offline data sync |

### Telemetry Data Format

{
  "hub_id": "string",
  "timestamp": "ISO-8601",
  "location": {
    "latitude": "double",
    "longitude": "double",
    "altitude": "double",
    "accuracy": "double"
  },
  "imu": {
    "acceleration_x": "double",
    "acceleration_y": "double",
    "acceleration_z": "double",
    "gyro_x": "double",
    "gyro_y": "double",
    "gyro_z": "double"
  },
  "speed": "double",
  "heading": "integer",
  "status": {
    "battery": "integer",
    "storage_used": "integer",
    "connection": "string"
  }
}

## Hardware Certification Requirements

| Requirement | Status | Responsible Party |
|-------------|--------|-------------------|
| ICASA (South Africa) | In Progress | Zanova Engineering |
| FCC (USA) | In Progress | Zanova Engineering |
| CE (Europe) | In Progress | Zanova Engineering |
| IC (Canada) | In Progress | Zanova Engineering |