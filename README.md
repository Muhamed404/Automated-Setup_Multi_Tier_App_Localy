# Automated Setup for Multi-Tier Java Web Application

## Project Overview

This project automates the provisioning of a multi-tier Java web application using Vagrant. It sets up an infrastructure comprising:

- **MariaDB (MySQL)**: Database layer for data persistence.
- **Memcached**: Caching mechanism for improving performance.
- **RabbitMQ**: Message broker for asynchronous communication.
- **Apache Tomcat**: Java web application server.
- **NGINX**: Reverse proxy and load balancer.
- **Maven**: Builds and packages the Java application.
- **Vagrant**: Provisions virtual machines and configures services.

This project is based on the Udemy course: [DevOps Projects](https://www.udemy.com/course/devopsprojects/).
The original GitHub repository for this project is available at: [vProfile Project](https://github.com/hkhcoder/vprofile-project).

## Architecture Overview

### Workflow:

1. **Users** send requests to **NGINX**.
2. **NGINX** forwards requests to **Apache Tomcat**.
3. **Tomcat** processes the request.
4. **MariaDB** stores and retrieves application data.
5. **RabbitMQ** queues messages for asynchronous processing.

## Setup Instructions

### Prerequisites

Ensure the following are installed on your system:

- Vagrant
- VirtualBox 
- Git (optional for cloning the repo)

### Installation

1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd Automated_provisioning_WinMacIntel
   ```
2. Start the environment:
   ```sh
   vagrant up
   ```
3. Once provisioning is complete, access the application at:
   ```
   http://<nginx--vm-ip-add>
   ```

## Vagrant Setup Details

- **Vagrantfile**: Defines VM configurations, networks, and provisioning steps.
- **Provisioning Scripts**:
  - `nginx.sh`: Installs and configures NGINX.
  - `tomcat.sh`: Installs and configures Apache Tomcat.
  - `mysql.sh`: Sets up MariaDB.
  - `memcache.sh`: Installs Memcached.
  - `rabbitmq.sh`: Installs RabbitMQ.

## Usage

- **Accessing the Web Application**: Once VMs are up, open `http://<nginx--vm-ip-add>`.
- **Database Access**: Use MariaDB with the configured credentials.
- **Message Queue Monitoring**: Check RabbitMQ queues for message processing.
- **Cache Invalidation**: Memcached handles automatic caching, reducing DB queries.

## Troubleshooting

- Run `vagrant status` to check VM statuses.
- Use `vagrant ssh <vm-name>` to access a specific VM.
- Restart services if necessary using `systemctl restart <service>`.
- Check logs for debugging:
  - **NGINX**: `/var/log/nginx/error.log`
  - **Tomcat**: `/var/log/tomcat9/catalina.out`
  - **MariaDB**: `/var/log/mysql/error.log`
  - **RabbitMQ**: `/var/log/rabbitmq/rabbit.log`

## Contributing

Feel free to submit issues or pull requests to enhance this automated setup.



