# DOCKER PROJECT

## Install Docker
```sh
yum install docker -y
systemctl start docker
systemctl status docker
```

## Dockerfile
```dockerfile
FROM ubuntu
RUN apt-get update -y
RUN apt-get install apache2 -y
COPY index.html /var/www/html/
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]
```

## 1. Create 3 Servers (T2.Medium) and Install Docker
```sh
yum install docker -y
systemctl start docker
systemctl status docker
docker swarm init --advertise-addr 172.31.85.110
docker node ls
```

## 2. Installing Jenkins (Master)
### Step 1: Install Git, Java 1.8.0, and Maven
```sh
yum install git java-1.8.0-openjdk maven -y
```

### Step 2: Get Jenkins Repository
```sh
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

### Step 3: Install Java 11 and Jenkins
```sh
amazon-linux-extras install java-openjdk11 -y
yum install jenkins -y
update-alternatives --config java
```

### Step 4: Start Jenkins
```sh
systemctl start jenkins.service
systemctl status jenkins.service
```

## 3. Create Custom Images and Push to DockerHub
### Dockerfile
```dockerfile
FROM ubuntu
RUN apt-get update -y
RUN apt-get install apache2 -y
COPY index.html /var/www/html/
CMD ["/usr/sbin/apachectl", "-D", "FOREGROUND"]
```

### index.html
(Create your HTML file here)

## 4. Set Permissions
```sh
chmod 777 /var/run/docker.sock
systemctl daemon-reload
systemctl restart docker.service
```

## 5. Write Compose File and Push to GitHub

## Setup Portainer
```sh
curl -L https://downloads.portainer.io/ce2-16/portainer-agent-stack.yml -o portainer-agent-stack.yml
docker stack deploy -c portainer-agent-stack.yml portainer
docker ps
```

### Access Portainer
```
public-ip of swarm master:9000
```

