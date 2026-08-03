# Hardware

## General notes on pins

The pins shown in the diagrams and tables are examples based on current configurations. Each installation may vary depending on the board model used (ESP32-S3, ESP32-C6, ESP32-C3, mini or standard format). Pins should be adapted to your own hardware and needs.

## The manifold

### Compatible microcontrollers

| Chip | Note |
|------|------|
| **ESP32-C6** | Currently used, supports WiFi + ESP-NOW |
| **ESP32-S3** | Valid alternative, more computing power |
| **ESP32-C3** | Compatible, fewer resources but sufficient |

### Components and functions

| Component | Quantity | Function |
|------------|----------|----------|
| Microcontroller | 1 | ESP32-C6/S3/C3 with WiFi + ESP-NOW |
| Relays | 4+ | Zone valve control |
| Relay | 1 | Circulator control |
| Optoisolators | 4+ | Valve feedback |
| LED | 1 | Status signaling |

### Operating logic

| Function | Description |
|----------|-------------|
| Command reception | Receives commands from thermostats via ESP-NOW or WiFi |
| Confirmations | Sends confirmations to thermostats |
| Alarms | Sends alarms in case of anomalies |
| Circulator management | Customizable timing logic |
| Safety timeout | Evaluates shutdown after a preset time |
| Consistency check | Perpetual verification between requested and actual state |
| Feedback | Reading optoisolators to verify valve status |

## The thermostats

### Compatible microcontrollers

| Chip | Note |
|------|------|
| **ESP32-S3** | Recommended for models with display (e.g. Zero mini format) |
| **ESP32-C6** | For models without display or with basic functionality |
| **ESP32-C3** | For compact models or repeaters |

### Models and installations

| Model | Installation | Specific function |
|---------|---------------|-------------------|
| **Mobile** | Electrical outlet | Plug-and-play, standard solution |
| **Internal 503** | Inside 503 box | Local user interface |
| **Side 503** | Side-mounted on 503 box | Compact module, essential controls |
| **Repeater** | Side or inside 503 | ESP-NOW network extension |
| **Panel** | Side or inside 503 | Centralized control, full menu |

### Common features

| Component | Function |
|------------|----------|
| Microcontroller | Processing and communication (S3, C6 or C3) |
| Sensor | Temperature and humidity sensing |
| LED | Status signaling |
| Communication | WiFi + ESP-NOW (primary and fallback) |
