# DevOps CI/CD Pipeline with Jenkins & Docker

This project demonstrates a complete **CI/CD pipeline** using **Jenkins** and **Docker** to automatically build, test, containerize, and deploy a simple Python Flask web application.

The goal of this project is to showcase **modern DevOps best-practices** including:

✔ Continuous Integration  
✔ Continuous Deployment  
✔ Pipeline-as-Code  
✔ Containerized builds  
✔ Automated testing  

---

## 🚀 Architecture Overview

GitHub Repo → Jenkins Pipeline → Test → Docker Build → Deploy Container


- Jenkins runs in Docker  
- The application also runs in Docker  
- The pipeline is defined in a `Jenkinsfile`

This ensures **reliable, repeatable, automated delivery**.

---

## 📦 Technology Stack

| Component | Purpose |
|----------|--------|
| Python (Flask) | Web application |
| Pytest | Unit testing |
| Docker | Containerization |
| Jenkins | CI/CD automation |
| Declarative Pipeline | Pipeline as Code |

---

## 🧠 Application Summary

The application is a simple Flask API that returns a message confirming successful deployment.

Endpoint:

GET /


Response:

CI/CD Pipeline working successfully!


---

## 📂 Project Structure

.
├── app
│ ├── server.py
│ ├── requirements.txt
│ ├── tests
│ │ └── test_app.py
│ └── Dockerfile
└── Jenkinsfile


---

## ⚙ Flask Application

`server.py` runs a lightweight web server on port **5000**.

---

## 🧪 Unit Testing

We use **pytest** to verify the `/` route returns HTTP 200.

The pipeline fails if tests fail.

This enforces **Continuous Integration**.

---

## 🐳 Docker Image

The app is packaged into a Docker image using the included `Dockerfile`.

This ensures:

✔ consistent builds  
✔ reproducible environments  
✔ portability  

---

## 🔄 Jenkins CI/CD Pipeline

The pipeline is defined in **Jenkinsfile**:

### Pipeline Stages

| Stage | Description |
|-------|-------------|
| Checkout | Pull source code from GitHub |
| Install & Test | Run tests inside a Python Docker container |
| Build Docker Image | Build application image |
| Run Container | Deploy latest version |

---

## 🧪 Stage 1 — Checkout

Jenkins pulls code from GitHub via SCM configuration.

---

## 🧪 Stage 2 — Install & Test (CI)

Dependencies are installed and tests run inside:

python:3.10-slim


If tests fail → pipeline stops.

---

## 🏗 Stage 3 — Build Docker Image

Example image name:

sample-devops-app:latest


---

## 🚀 Stage 4 — Deploy Container

Runs the container on port **5000**.

Access app via:

http://localhost:5000


---

## 🎯 Key DevOps Concepts Demonstrated

- Continuous Integration
- Continuous Deployment
- Pipeline-as-Code
- Test Automation
- Dockerized workloads
- Immutable builds
- Clean environment isolation

This workflow mirrors **real production DevOps pipelines**.

---

## 🧑‍💻 How To Run Locally

Install dependencies:

pip install -r requirements.txt


Run app:

python server.py


Visit:

http://localhost:5000


---

## 🐳 Build & Run Docker Manually (Optional)

docker build -t sample-devops-app .
docker run -p 5000:5000 sample-devops-app


---

## 🏆 Why This Project Matters

This project demonstrates:

✔ automation  
✔ reliability  
✔ testing discipline  
✔ deployment consistency  

All essential skills for a **DevOps Engineer**.

---

## 👤 Author

Mahesh raj V

---

## ✅ Status

✔ W
