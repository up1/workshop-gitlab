# Workshop :: GitLab and GitLab CI
* Docker
* Linux :: Ubuntu server

## 1. Start GitLab server
```
$docker compose up -d gitlab-server

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

## 3. Add GitLab CI runner in GitLab Server
```
$gitlab-runner register  --url http://localhost:8000  \
                        --token glrt-ydjvGwY6HqXrtBwz9Myh
```