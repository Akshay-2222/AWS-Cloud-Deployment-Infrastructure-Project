# AWS Cloud Deployment & Infrastructure Project

Hello! This is my AWS Cloud Deployment & Infrastructure Project. For this project, I took a standard MEAN stack application and built a complete, automated cloud deployment pipeline from scratch. 

This project was a great hands-on experience in cloud infrastructure, containerization, and automation. Below is a breakdown of how I approached the task and the solutions I implemented.

## Technology Stack
* **Application:** Angular (Frontend), Node.js/Express (Backend), MongoDB (Database)
* **Containerization:** Docker & Docker Compose
* **Cloud Provider:** AWS (EC2 Ubuntu Instance)
* **Web Server:** Nginx (Reverse Proxy)
* **CI/CD:** GitHub Actions & Docker Hub

---

## My Approach & Problem Solving

### 1. Containerizing the Application
To make sure the application runs perfectly on any machine without installation issues, I containerized it. I wrote a `Dockerfile` for both the Angular frontend and the Node.js backend. Then, I used `docker-compose.yml` to link the frontend, backend, and MongoDB database together so they can communicate smoothly on the same network.

### 2. Cloud Hosting on AWS
I provisioned a free-tier Ubuntu EC2 instance on AWS to host the project. To keep the server secure, I configured the AWS Security Groups to only allow necessary traffic: Port 80 for public web access and Port 22 so I could securely manage the server via SSH.

### 3. Solving the RAM Crash (Linux Swap Space)
**The Challenge:** The free AWS instance only has 1GB of RAM. Whenever I tried to build the Angular frontend, the server would run out of memory and freeze completely.
**The Solution:** Instead of upgrading to a paid server, I solved this by configuring a 2GB Linux Swap file. This allowed the server to use the hard drive as temporary RAM, and the build process finished flawlessly.

### 4. Setting up a Reverse Proxy
By default, the Docker containers were running on specific ports (like 8081). Because it's not professional to have users type port numbers into a URL, I installed Nginx. I configured Nginx to act as a reverse proxy—it sits at the front door (Port 80) and seamlessly routes incoming web traffic to the hidden Docker containers.



### 5. Automating with a CI/CD Pipeline
To avoid logging into the server manually every time I update the code, I built a Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions. 
Now, whenever code is pushed to the `main` branch, my workflow automatically:
1. Builds fresh Docker images.
2. Pushes them securely to Docker Hub.
3. SSHs into the AWS EC2 server.
4. Pulls the new images and safely restarts the application.



---

## 💻 Running the Project Locally

If you'd like to test my setup on your local machine, run the following commands:

1. Clone this repository:
   ```bash
   git clone [https://github.com/Akshay-2222/AWS-Cloud-Deployment-Infrastructure-Project]
   cd AWS-Cloud-Deployment-Infrastructure-Project

2.Build and start the containers:
docker-compose up -d --build

3.View the application in your browser:

Frontend: http://localhost:8081

Backend API: http://localhost:8080




<img width="1402" height="352" alt="Screenshot 2026-02-24 at 10 11 07 PM" src="https://github.com/user-attachments/assets/4333ae0d-8a77-4624-8502-5300fa4ff656" />

<img width="1410" height="519" alt="Screenshot 2026-02-24 at 10 10 47 PM" src="https://github.com/user-attachments/assets/5400d0b1-53ff-4248-9691-38028ade0515" />

<img width="1429" height="310" alt="Screenshot 2026-02-24 at 10 10 18 PM" src="https://github.com/user-attachments/assets/19e1afc4-df9d-4e70-bc76-a0b0be1d71db" />

<img width="1421" height="377" alt="Screenshot 2026-02-24 at 10 09 40 PM" src="https://github.com/user-attachments/assets/da4a99ec-6fc9-4290-9719-3ae0dc73e926" />
