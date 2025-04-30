# OpenVUS

OpenVUS is a Docker-based setup for deploying the Greenbone Community Edition (GCE), a comprehensive vulnerability management system. This repository provides a pre-configured `docker-compose.yml` file and setup guide to quickly deploy and manage the system.

---

## Features

- **Greenbone Vulnerability Management (GVM)**: Includes services such as vulnerability tests, data management, and reporting.
- **Greenbone Security Assistant (GSA)**: A web-based interface for managing scans and reports.
- **OpenVAS**: An open-source vulnerability scanner.
- **Persistent Data Storage**: Uses Docker volumes to ensure data is retained across container restarts.

---

## Prerequisites

Before using this repository, ensure the following are installed:

1. **Docker**: [Download and install Docker](https://docs.docker.com/get-docker/).
2. **Docker Compose**: [Install Docker Compose](https://docs.docker.com/compose/install/).
3. **Git**: Clone this repository using Git.

---

## Installation

### Step 1: Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/boniyeamincse/openvus.git
cd openvus
```

### Step 2: Start the Services

Run the following command to start all services:

```bash
docker-compose up -d
```

This will pull the required Docker images and start the containers in detached mode.

---

## Accessing the System

### Greenbone Security Assistant (GSA)

Once the services are running, access the GSA web interface in your browser:

```
http://127.0.0.1:8080
```

- **Host Port**: `8080`
- **Container Port**: `9392`

---

## Stopping the Services

To stop all running containers and clean up the environment, use:

```bash
docker-compose down
```

---

## Components Overview

The system comprises the following key components:

| Service Name           | Description                                    |
|------------------------|------------------------------------------------|
| `vulnerability-tests`  | Handles vulnerability test data.               |
| `notus-data`           | Manages Notus vulnerability data.              |
| `scap-data`            | Handles SCAP data.                             |
| `cert-bund-data`       | Manages CERT Bund data.                        |
| `dfn-cert-data`        | Manages DFN CERT data.                         |
| `data-objects`         | Processes data objects for GVM.                |
| `report-formats`       | Handles reporting formats.                     |
| `gpg-data`             | Manages GPG data for GVM.                      |
| `redis-server`         | Redis server for caching and data handling.    |
| `pg-gvm`               | PostgreSQL database for GVM.                   |
| `gvmd`                 | Greenbone Vulnerability Manager Daemon.        |
| `gsa`                  | Greenbone Security Assistant (web interface). |
| `openvas`              | Handles OpenVAS logs and configuration.        |
| `openvasd`             | OpenVAS Daemon for scanning.                   |
| `ospd-openvas`         | OSP protocol wrapper for OpenVAS.              |
| `gvm-tools`            | CLI tools for managing GVM.                    |

---

## Data Persistence

The following Docker volumes are used for persistent data storage:

- `gpg_data_vol`
- `scap_data_vol`
- `cert_data_vol`
- `data_objects_vol`
- `gvmd_data_vol`
- `psql_data_vol`
- `vt_data_vol`
- `notus_data_vol`
- `psql_socket_vol`
- `gvmd_socket_vol`
- `ospd_openvas_socket_vol`
- `redis_socket_vol`
- `openvas_data_vol`
- `openvas_log_data_vol`

---

## Troubleshooting

1. **Check Logs**: Use `docker-compose logs -f` to view logs of the running services.
2. **Restart Services**: Restart a specific service using:
    ```bash
    docker-compose restart <service-name>
    ```
3. **Firewall**: Ensure the host port `8080` is open and not blocked by a firewall.

---

## Contributing

Contributions are welcome! If you'd like to improve this setup or add new features:

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Submit a pull request with a detailed description of your changes.

---

## License

This repository is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this project as per the terms of the license.

---

## Acknowledgments

Special thanks to the Greenbone Community for providing the Greenbone Community Edition (GCE) and related tools.

For more information, visit the [Greenbone Community Documentation](https://greenbone.github.io/).
