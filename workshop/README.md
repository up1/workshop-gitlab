# Workshop :: GitLab and GitLab CI
* Docker
* Linux :: Ubuntu server

## 1. Start GitLab server
```
$docker compose up -d gitlab-server
$docker compose logs -f

// Waiting .... 3-5 minutes
$docker compose ps
NAME            IMAGE                     COMMAND             SERVICE         CREATED         STATUS                   PORTS
gitlab-server   gitlab/gitlab-ce:latest   "/assets/wrapper"   gitlab-server   4 minutes ago   Up 4 minutes (healthy)   22/tcp, 80/tcp, 443/tcp, 0.0.0.0:8000->8000/tcp, :::8000->8000/tcp
```
Access to GitLab UI
* http://localhost:8000
  * email=admin@demo.com
  * password=Abcd@0123456789
* Learn features
  * Git repository
  * Issue tracker
  * Merge Request (MR)

## 2. Start GitLab CI
```
$docker compose up -d gitlab-runner
$docker compose ps
```

## 3. Add GitLab CI runner
* Goto project settings -> CI/CD -> Runners

```
# Download the binary for your system
sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

# Give it permission to execute
sudo chmod +x /usr/local/bin/gitlab-runner

# Create a GitLab Runner user
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash

# Install and run as a service
sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
sudo gitlab-runner start

# Register
sudo gitlab-runner register --url http://localhost:8000 --registration-token GR1348941DaFqy98J5Zt9WgvPu9ye
```