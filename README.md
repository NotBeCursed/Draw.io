# Draw.io - Self-hosted Diagramming Tool

This repository provides a simple Docker configuration to deploy **Draw.io** (also known as **diagrams.net**), an open-source web-based diagramming tool, on your server. With this setup, you can run a self-hosted instance of Draw.io for creating flowcharts, network diagrams, UML diagrams, and more.

## Prerequisites

Before using this repository, make sure you have the following installed on your system:

- Docker (latest version)
- Docker Compose (if you prefer using a Compose file)

## Features

- Create flowcharts, process diagrams, UML diagrams, and network diagrams.
- Fully self-hosted solution.
- Secure access via HTTPS (optional, but recommended).
- Simple and easy deployment using Docker.

## Installation

Follow these steps to deploy your own instance of **Draw.io**:

### 1. Clone the repository

Clone this repository to your local machine:

```bash
git clone https://github.com/NotBeCursed/Draw.io.git
cd Draw.io
```

### 2. Modify configuration (optional)

If you want to change any configuration, such as ports, you can modify the `docker-compose.yml` or Docker settings in the repository.

For example, if you want to map the container’s ports to different host ports, you can change the `ports` section in the `docker-compose.yml` file:

```yaml
services:
  drawio:
    container_name: drawio
    hostname: drawio
    image: jgraph/drawio
    restart: unless-stopped
    ports:
      - 8080:8080 # Web interface
      - 8443:8443 # Secure web interface (optional)
```

### 3. Start the container

Start your Draw.io container with the following command:

```bash
docker-compose up -d
```

If you are using just Docker (without Compose), you can use this:

```bash
docker run -d -p 8080:8080 -p 8443:8443 --name drawio jgraph/drawio
```

### 4. Access Draw.io

Once the container is running, you can access **Draw.io** through your browser:

- **HTTP**: [http://localhost:8080](http://localhost:8080)
- **HTTPS** (if enabled): [https://localhost:8443](https://localhost:8443)

### 5. Optional: Set up SSL (HTTPS)

For better security, it is recommended to set up SSL (HTTPS) for your Draw.io instance. You can either set up a reverse proxy with Nginx or use a service like [Let's Encrypt](https://letsencrypt.org/) to obtain a free SSL certificate.

## Usage

After accessing the web interface, you can start creating your diagrams. The application supports the following features:

- Drag-and-drop interface.
- Multiple templates and shapes.
- Export options in various formats (PNG, SVG, PDF, etc.).
- Integration with cloud storage services (Google Drive, OneDrive, etc.).

## Troubleshooting

If you face any issues, try the following steps:

1. **Check logs**:
   To view the logs for the Draw.io container, use the following command:

   ```bash
   docker logs drawio
   ```

2. **Check for errors during startup**:
   If the application isn't accessible, ensure that the ports are not blocked by a firewall, and check if the container is running with:

   ```bash
   docker ps
   ```

3. **Permissions issues**:
   Ensure that the directories used by the container (if any) have the correct permissions for the container user.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
