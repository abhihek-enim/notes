# Docker Commands Guide

## 🚀 Introduction
This document covers essential Docker commands, categorized from basic to advanced, along with real-world use cases.

---

## **🟢 1. Basic Docker Commands (Essential for Beginners)**  

### 🔹 **Check Docker Version**  
```sh
docker --version
```
📌 *Verify Docker installation.*

### 🔹 **Pull an Image**  
```sh
docker pull ubuntu
```
📌 *Download the latest Ubuntu image for containerized environments.*

### 🔹 **List Downloaded Images**  
```sh
docker images
```
📌 *Check available images before creating containers.*

### 🔹 **Run a Container (Interactive Mode)**  
```sh
docker run -it ubuntu bash
```
📌 *Start an Ubuntu container and interact via Bash.*

### 🔹 **Run a Container in Detached Mode**  
```sh
docker run -d nginx
```
📌 *Run an Nginx web server in the background.*

### 🔹 **List Running Containers**  
```sh
docker ps
```
📌 *See active containers and their status.*

### 🔹 **List All Containers (Including Stopped Ones)**  
```sh
docker ps -a
```
📌 *View historical containers for debugging.*

### 🔹 **Stop a Running Container**  
```sh
docker stop container_id
```
📌 *Gracefully shut down a running application.*

### 🔹 **Remove a Stopped Container**  
```sh
docker rm container_id
```
📌 *Clean up old containers to free disk space.*

### 🔹 **Remove an Image**  
```sh
docker rmi image_id
```
📌 *Delete unnecessary images to optimize storage.*

---

## **🟡 2. Intermediate Docker Commands (Day-to-Day Usage)**  

### 🔹 **Run a Container and Remove It After Exit**  
```sh
docker run --rm ubuntu echo "Hello from Docker"
```
📌 *Execute one-time tasks like checking environment variables.*

### 🔹 **Map a Local Port to a Container's Port**  
```sh
docker run -d -p 8080:80 nginx
```
📌 *Expose an Nginx web server on port 8080.*

### 🔹 **Restart a Container**  
```sh
docker restart container_id
```
📌 *Restart an application without creating a new container.*

### 🔹 **View Logs of a Running Container**  
```sh
docker logs container_id
```
📌 *Debug application issues by checking logs.*

### 🔹 **Follow Logs in Real-Time**  
```sh
docker logs -f container_id
```
📌 *Monitor an application continuously.*

### 🔹 **Execute Commands in a Running Container**  
```sh
docker exec -it container_id bash
```
📌 *SSH into a container to inspect its environment.*

### 🔹 **Copy Files Between Host and Container**  
```sh
docker cp file.txt container_id:/app/file.txt
```
📌 *Transfer configuration files into a running container.*

---

## **🟠 3. Advanced Docker Commands (For Production & Scaling)**  

### 🔹 **Build a Docker Image from a Dockerfile**  
```sh
docker build -t myapp:latest .
```
📌 *Package an application with all dependencies for deployment.*

### 🔹 **Run a Container with Persistent Storage**  
```sh
docker run -d -v my_volume:/data ubuntu
```
📌 *Store database files or logs persistently.*

### 🔹 **Inspect a Container's Configuration & Metadata**  
```sh
docker inspect container_id
```
📌 *Retrieve network settings, environment variables, and mounts.*

### 🔹 **Remove All Unused Images**  
```sh
docker image prune -a
```
📌 *Clean up outdated images and reclaim disk space.*

---

## **🔵 4. Docker Networking & Multi-Container Applications**  

### 🔹 **Create a Custom Network**  
```sh
docker network create my_network
```
📌 *Allow multiple containers to communicate internally.*

### 🔹 **Run a Container on a Custom Network**  
```sh
docker run -d --network my_network --name my_container nginx
```
📌 *Isolate applications for better security.*

### 🔹 **List All Networks**  
```sh
docker network ls
```
📌 *Manage different networks for microservices.*

---

## **🟣 5. Docker Compose Commands (Managing Multi-Container Apps)**  

### 🔹 **Start All Services in the Background**  
```sh
docker-compose up -d
```
📌 *Deploy a full stack app (backend, database, frontend) easily.*

### 🔹 **Stop All Services**  
```sh
docker-compose down
```
📌 *Shut down an application stack cleanly.*

### 🔹 **Rebuild Services and Restart**  
```sh
docker-compose up --build -d
```
📌 *Apply changes after modifying a Dockerfile.*

### 🔹 **Check Logs for All Services**  
```sh
docker-compose logs -f
```
📌 *Debug issues in a multi-container environment.*

### 🔹 **Scale Services Up or Down**  
```sh
docker-compose up --scale web=3
```
📌 *Run multiple instances of a service (useful for load balancing).*

---

## **🔴 6. Docker System Maintenance & Cleanup**  

### 🔹 **Remove All Containers, Images, Networks & Volumes**  
```sh
docker system prune -a --volumes
```
📌 *Completely clean up Docker when running out of disk space.*

### 🔹 **Show Running and Stopped Containers with Disk Usage**  
```sh
docker ps -as
```
📌 *See how much space each container is consuming.*

---

## **🎯 Final Thoughts**  
- **Basic Commands:** Running and managing containers.
- **Intermediate Commands:** Working with logs, volumes, and networking.
- **Advanced Commands:** Building, deploying, scaling, and optimizing containers.

🚀 Master these, and you’ll be **Docker-proficient in real-world projects!**
