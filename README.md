# DOCKER-NGINX-HTTP3-REVERSE-RPOXY

## Introduction

**NGINX HTTP/3 Docker Demo** is a demonstration project designed to showcase the setup of NGINX with HTTP/3 support using Docker. This project provides a comprehensive example of how to configure NGINX to utilize the latest HTTP/3 protocol, offering enhanced performance and security features over previous versions.

In this demo project, you will find:

* **Step-by-Step Setup**: Instructions for configuring NGINX within a Docker container to support HTTP/3.
* **Reverse Proxy Configuration**: Guidance on how to use NGINX as a reverse proxy to manage incoming traffic effectively.
* **Docker Integration**: A pre-configured Docker environment to streamline the deployment process and ensure a consistent setup across different systems.

Whether you're looking to explore HTTP/3 features or set up a reverse proxy for your own applications, this demo provides a solid foundation and practical examples to help you get started quickly and efficiently.

For a more detailed guide on getting the demo up and running, please refer to the [Usage](#usage) section.

## Usage
1. **Configure SSL certificate**
* **If you own your own SSL certificate**:

    1. Put SSL certificate into `.docker/nginx/ssl/fullchain.pem` and SSL Certificate Key into `.docker/nginx/ssl/privkey.pem`.

* **If you don't own your own SSL certificate**: Use the following guide to generate a self-signed SSL certificate for testing purposes:

    1.
        ```bash
        docker build -f Dockerfile.mkcert . -t mkcert:latest
        ```
    2.
        ```bash
        docker run -v /$(pwd)/.docker/nginx/ssl:/root/.local/share/mkcert/ mkcert:latest bash -c "mkcert -install -cert-file /root/.local/share/mkcert/fullchain.pem -key-file /root/.local/share/mkcert/privkey.pem localhost"
        ```

        This command will generate the following files:
        ```
        .docker/nginx/ssl/fullchain.pem`: The SSL certificate file.
        .docker/nginx/ssl/privkey.pem`: The SSL certificate key file.
        .docker/nginx/ssl/rootCA.pem`: The root CA certificate.
        .docker/nginx/ssl/rootCA-key.pem`: The private key for the root CA certificate.
        ```
    **Important**: The `rootCA.pem` needs to be added to your system's trust store to prevent browser warnings about the self-signed certificate. For detailed instructions on how to do this, please refer to the [Adding CA Certificate to Trust Store](docs/add_to_trust_store.md) guide.

1. **Create Docker network**
    ```bash
    docker network create nginx-http3
    ```
1. **Run the application**
    ```bash
    docker-compose up
    ```
1. **Open the Application**
    * Once the application is up and running, open your web browser and navigate to `https://localhost` (or the relevant URL if you configured a different one).
    * You should see the demo application running with HTTP/3 support enabled.

    If you encounter any issues, ensure that Docker and Docker Compose are properly installed and running, and check the logs for any errors.
