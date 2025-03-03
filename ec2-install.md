# Docker and Docker Compose Setup on EC2

This guide will help you install Docker and Docker Compose on a newly created EC2 instance, and resolve potential permission issues when running `docker-compose up -d`.

## Step 1: Update the Package Repository
SSH into your EC2 instance and update the package repository.

**Ubuntu:**
```bash
sudo apt-get update
```

## Step 2: Install Docker

**Ubuntu:**
```bash
sudo apt-get install docker.io -y
```

## Step 3: Start Docker and Enable It on Startup

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

## Step 4: Add Your User to the Docker Group (Optional but Recommended)

To avoid using `sudo` with Docker commands:

```bash
sudo usermod -aG docker $USER
```

Log out and log back in, or use:

```bash
newgrp docker
```

## Step 5: Install Docker Compose

1. Download the latest Docker Compose binary:

    ```bash
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.29.7/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    ```

2. Apply executable permissions:

    ```bash
    sudo chmod +x /usr/local/bin/docker-compose
    ```

3. Verify the installation:

    ```bash
    docker-compose --version
    ```

## Step 6: Test Docker Compose

Create a simple `docker-compose.yml` file to test:

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "80:80"
```

Run it with Docker Compose:

```bash
docker-compose up -d
```
try `http://${HOST}`
