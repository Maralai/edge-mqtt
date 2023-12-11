# README for Mosquitto Docker Application

## Overview

This application sets up a Mosquitto MQTT broker using Docker. Mosquitto is an open-source message broker that implements the MQTT protocol. It's designed for lightweight and efficient messaging, making it ideal for IoT and device communication. This setup includes Docker configurations and scripts to manage the Mosquitto service.

### Directory Structure

```
.
├── .env
├── .gitignore
├── docker-compose.yaml
├── LICENSE
├── README.md
└── mosquitto/
    ├── entrypoint.sh
    └── config/
        └── mosquitto.conf
```

- `.env`: Environment variables file.
- `.gitignore`: Specifies intentionally untracked files to ignore.
- `docker-compose.yaml`: Docker Compose configuration file.
- `LICENSE`: The license file for the project.
- `README.md`: This file, providing documentation.
- `mosquitto/`: Directory containing Mosquitto broker configurations.
  - `entrypoint.sh`: Entrypoint script for the Docker container.
  - `config/`: Contains Mosquitto configuration files.
    - `mosquitto.conf`: Mosquitto broker configuration file.

## Getting Started

### Prerequisites

- Docker and Docker Compose installed.
- Basic knowledge of MQTT protocol and Docker usage.

### Installation

1. Clone the repository to your local machine.
2. Navigate to the root directory of the project.
3. Configure the `.env` file with necessary environment variables.
4. Run `docker-compose up` to start the Mosquitto MQTT broker.

### Configuration

- **Mosquitto Configuration (`mosquitto.conf`)**: Configures the MQTT broker, including persistence settings, logging, listeners for MQTT and WebSockets, and bridge configuration.
- **Entrypoint Script (`entrypoint.sh`)**: Manages the creation and updating of `passwords.txt` for MQTT authentication, modifies `mosquitto.conf` based on environment variables, and starts the Mosquitto broker.

#### Environment Variables

- `MQTT_USERNAME` and `MQTT_PASSWORD`: Credentials for MQTT users.
- `REMOTE_SERVER`, `REMOTE_PORT`, `REMOTE_USERNAME`, `REMOTE_PASSWORD`, and `DEVICE_ID`: Used for configuring MQTT bridge to a remote broker.

Example .env file (CHANGE USERNAME & PASSWORDS!)

```bash
# device name for 
DEVICE_ID=this_device
MQTT_USERNAME=this_mqtt_user
MQTT_PASSWORD=this_mqtt_pass

# Bridge Configuration - This section will be modified or removed based on environment variables in entrypoint script
# The bridge configuration allows Mosquitto to connect to a remote MQTT broker and forward messages between the two brokers.

# Set the REMOTE_SERVER variable below to connect this as a node.
# REMOTE_SERVER=your_mqtt_server
# REMOTE_USERNAME=your_mqtt_username
# REMOTE_PASSWORD=your_mqtt_password
# REMOTE_PORT=your_mqtt_port
```

### Usage

- After running `docker-compose up`, the Mosquitto broker will be available on the specified ports for MQTT and WebSocket connections.
- Clients can connect to the broker using the MQTT protocol or WebSockets.
- The broker can also connect to a remote MQTT broker as a bridge if configured.

## License

This project is licensed under [LICENSE]. Please refer to the license file for details.

## Contributing

Contributions to this project are welcome. Please follow standard GitHub pull request procedures.

## Support

For support and queries, please open an issue in the GitHub repository.

---

*Note: This README assumes a certain level of familiarity with MQTT, Docker, and Docker Compose. Users are expected to have basic knowledge of these technologies to effectively use this application.*