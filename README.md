AI-Powered Sentiment Analysis with Secure CI/CD Deployment
📌 Overview

This project implements an end-to-end AI-powered sentiment analysis service, with the primary focus on production-grade software engineering and deployment practices rather than standalone model development.

The core ML component uses a Scikit-learn classifier to categorize text (reviews, tweets, social media posts, etc.) as positive, negative, or neutral. The model is wrapped in a Flask REST API, containerized with Docker, and shipped through a secure, automated CI/CD pipeline to a live cloud endpoint on AWS SageMaker.

This project demonstrates how a machine learning model moves from a local script to a scalable, secure, cloud-hosted service — the same way real-world software teams ship AI products.

🎯 Objectives (Course Outcomes)
CO	Area	How it's demonstrated
CO1	Agile Methodology	Sprint planning and task tracking via Trello
CO2	DevOps Automation	Docker, Git, and GitHub Actions CI/CD pipeline
CO3	DevSecOps	Automated security gates using SonarCloud and Trivy
CO4	MLOps / Cloud Deployment	Live deployment to AWS SageMaker
🧱 Project Architecture
Text Input → Flask API (/predict) → Scikit-learn Model → Sentiment Output
                        │
                        ▼
                  Dockerized App
                        │
                        ▼
              GitHub Actions CI/CD
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
  Docker Build    SonarCloud Scan   Trivy Scan
        │               │               │
        └───────────────┴───────────────┘
                        ▼
              AWS SageMaker Deployment
                        │
                        ▼
              Live Endpoint + Monitoring
⚙️ Tech Stack
Language: Python
ML Library: Scikit-learn
API Framework: Flask
Containerization: Docker
Version Control: Git & GitHub
CI/CD: GitHub Actions
Code Quality: SonarCloud
Security Scanning: Trivy
Cloud Deployment: AWS SageMaker
Project Management: Trello (Agile/Scrum)
🚀 Workflow
Plan the work — Tasks broken into sprints and tracked on Trello following Agile/Scrum principles.
Train the model — A Scikit-learn classifier is trained on labeled review data (e.g., IMDB dataset) to predict sentiment.
Build the API — A Flask app exposes a /predict endpoint that accepts text input and returns the predicted sentiment.
Containerize — A Dockerfile packages the app, model, and dependencies into a portable container image.
Push to GitHub — All code, configs, and the Dockerfile live in this repository; every push triggers the CI/CD pipeline.
CI/CD Pipeline (GitHub Actions) — On every push:
Builds the Docker image
Runs SonarCloud for code quality analysis
Runs Trivy for container vulnerability scanning
Proceeds to deployment only if all checks pass
Deploy — On a successful pipeline run, the app is deployed to AWS SageMaker as a live endpoint.
Monitor — A basic /health endpoint and logs provide visibility into uptime, response time, and usage after deployment.
📁 Repository Structure
├── app/
│   ├── app.py              # Flask application (API entry point)
│   ├── model/               # Trained Scikit-learn model artifact(s)
│   └── requirements.txt     # Python dependencies
├── Dockerfile                # Container build definition
├── .github/
│   └── workflows/
│       └── ci-cd.yml         # GitHub Actions pipeline (build, scan, deploy)
├── docs/
│   └── trello-screenshots/   # Sprint planning evidence
└── README.md
🔌 API Usage

Endpoint: POST /predict

Request:

json
{
  "text": "This movie was absolutely fantastic!"
}

Response:

json
{
  "sentiment": "positive"
}

Health Check: GET /health

json
{
  "status": "ok"
}
🔒 Security & Quality Gates

Every code push automatically runs through:

SonarCloud — Static code analysis for bugs, code smells, and maintainability issues.
Trivy — Vulnerability scanning of the Docker image for known CVEs in dependencies and base images.

The pipeline fails and stops deployment if any check does not pass, ensuring security is enforced automatically rather than checked manually.

☁️ Deployment

Once the pipeline confirms a clean, secure build, the application is deployed to AWS SageMaker, making the sentiment analysis service accessible as a live, hosted endpoint.

👥 Team — Batch 18
Name	Roll Number
Kongari Abhinav	2420030263
E. Hitesh	2420030576
P. Umesh	2420030027
M. Rakesh	2420030251
🔑 Keywords

Machine Learning · Cloud DevOps · CI/CD · DevSecOps · AWS SageMaker · Docker · Agile Methodology · Sentiment Analysis
