# Homelab
The homelab hosts the majority of my media and productivity services, along storage infrastructure for the network.


## Project Goals
- Build hands-on experience with Linux system administration, networking, and self-hosting.
- Develop and maintain a private platform for hosting personal applications and media services.
- Learn Docker and Docker Compose by deploying and managing containerized applications.
- Gain experience with storage management, file sharing, and media automation.
- Practice monitoring, troubleshooting, and maintaining a long-running Linux server.


## Environment
- Ubuntu Desktop 24.04 LTS
- Docker & Docker Compose
- Hosted on Personal Laptop 
- Large HDD External Mounted Storage


## Core Services

### Networking
- UFW: Netfilter firewall filter
- Tailscale: Secure remote access to the Homelab.

### Media
- Jellyfin: Media streaming server.
- Koel: Music streaming server.
- Kavita: eBook and comic server.

### Productivity
- Nextcloud: Self-Hosted Cloud Infrastructure 
- SMB Share: Network file sharing.
- MariaDB: SQL database.

### Monitoring
- Netdata: Real-time monitoring of system resources and services.
- Watchtower: Automatic Docker container updates.
- Portainer: Docker container management.
- ClamAV: Malware scanning for files and shared storage.


## Network
Remote access is provided through Tailscale, allowing secure access to applications without exposing them directly to the public internet. 

Services are containerized using Docker and communicate over dedicated Docker networks. 

DNS requests are securely forwarded to my VPS, where they are filtered by Pi-hole and resolved through Unbound with Cloudflared as a fallback.

The homelab also serves as the primary storage location for both local services and my VPS / personal network through network-mounted storage.


Key components:
- Tailscale for secure remote connection.
- DNS resolution / filtering provided by my VPS.
- Docker for running and isolating self-hosted services.
- User-defined Docker networks for service communication.
- SMB for sharing files across devices on the local network.
- Mounted storage serving as the central media and application storage for my personal network


## Security
The homelab is designed to work in tandem with my VPS so the VPS handles public facing services, while the Homelab only serves local network services and storage to remain isolated. 

By limiting access to only devices authenticated by Tailscale, this minimizes unnecessary network exposure while providing secure access to self-hosted services.

Key components:
- UFW: Default-deny firewall rules to limit access. 
- Fail2ban: Automatically blocks IP addresses after repeated failed login attempts.
- Tailscale for secure remote access without exposing services publicly.
- DNS filtering and resolution provided by my VPS using Pi-hole, Unbound, and Cloudflared.
- Docker network isolation to separate applications where appropriate.
- User and file permissions configured to control access to mounted storage.
- Regular system and container updates to keep software current.


## Docker Infrastructure
Docker is used to host and manage the applications running on the homelab.

Each application runs in its own container with persistent storage to preserve data across updates and restarts.

My Docker environment includes:
- Docker Compose to define and manage multi-container applications.
- User-defined Docker networks to isolate services and control communication.
- Configuration files organized into separate directories for easier maintenance and deployment.
- Sensitive compose configuration separated into local .env files.
- Persistent volumes for application data and configuration.
- Watchtower for automatic container updates.


## Storage
The homelab provides the primary storage for media, application data, and shared files.

A large HDD mounted storage drive is used to centralize media libraries and persistent application data for self-hosted services. 

This storage is also shared with my VPS/other personal devices over the network, allowing services running on both systems to access the same files while keeping storage managed from a single location.



## Monitoring
The homelab is monitored to ensure applications and system resources remain healthy and available.

Netdata provides real-time visibility into CPU, memory, disk, network, and Docker performance. 

ClamAV is used to scan files and shared storage for malware. 

When troubleshooting issues, I also use Docker container logs and Linux system logs to diagnose application and system problems.


## Future Goals
- Expand monitoring and alerting across all self-hosted services.
- Implement automated backup and recovery for application data.
- Increase infrastructure automation using scripts and Docker Compose.
- Explore Kubernetes and container orchestration.
- Integrate cloud services with the homelab environment.
