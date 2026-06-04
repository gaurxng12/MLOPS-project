# 🚗 Vehicle Insurance Cross-Sell Prediction

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-green?logo=fastapi)
![Docker](https://img.shields.io/badge/Docker-Containerized-blue?logo=docker)
![AWS](https://img.shields.io/badge/AWS-EC2%20%7C%20S3%20%7C%20ECR-orange?logo=amazonaws)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green?logo=mongodb)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-black?logo=githubactions)

---

# 📌 Overview

This project is a production-oriented **MLOps pipeline** that predicts whether an existing health insurance customer is likely to purchase **vehicle insurance**.

The solution automates the complete machine learning lifecycle, including data ingestion, validation, preprocessing, model training, evaluation, model versioning, deployment, and inference. The application is containerized with Docker, deployed on AWS, and automated through a CI/CD pipeline using GitHub Actions.

---

# 🎯 Business Problem

Insurance companies often maintain large customer bases for health insurance products. Rather than approaching every customer with vehicle insurance offers, they can use machine learning to identify customers who are most likely to be interested.

By predicting customer interest in vehicle insurance, businesses can:

* Improve conversion rates
* Reduce unnecessary marketing costs
* Prioritize high-value prospects
* Increase cross-sell revenue

**Target Variable**

* `Response = 1` → Customer is interested in vehicle insurance
* `Response = 0` → Customer is not interested

---

# ✨ Key Features

* End-to-end ML training pipeline
* Automated data validation
* Data preprocessing and feature transformation
* Class imbalance handling using SMOTEENN
* Random Forest-based prediction model
* Model versioning using AWS S3
* FastAPI-based inference service
* Interactive prediction UI using HTML templates
* Dockerized deployment
* CI/CD automation using GitHub Actions
* AWS EC2 deployment

---

# 🏗️ Architecture

```text
MongoDB Atlas
      │
      ▼
Data Ingestion
      │
      ▼
Data Validation
      │
      ▼
Data Transformation
      │
      ▼
Model Training
      │
      ▼
Model Evaluation
      │
      ▼
Model Registry (AWS S3)
      │
      ▼
FastAPI Application
      │
      ▼
Docker → ECR → EC2
```

---

# 🛠️ Tech Stack

| Category            | Technology        |
| ------------------- | ----------------- |
| Language            | Python 3.10       |
| Machine Learning    | Scikit-Learn      |
| Data Processing     | Pandas, NumPy     |
| Imbalanced Learning | SMOTEENN          |
| API Framework       | FastAPI           |
| Frontend            | HTML, CSS, Jinja2 |
| Database            | MongoDB Atlas     |
| Cloud Storage       | AWS S3            |
| Containerization    | Docker            |
| Container Registry  | AWS ECR           |
| Deployment          | AWS EC2           |
| CI/CD               | GitHub Actions    |
| Serialization       | Dill              |

---

# 📊 Dataset

The dataset contains customer information collected from health insurance policyholders.

### Features

| Feature              | Description                       |
| -------------------- | --------------------------------- |
| Gender               | Customer gender                   |
| Age                  | Customer age                      |
| Driving_License      | Driving license availability      |
| Region_Code          | Customer region                   |
| Previously_Insured   | Existing vehicle insurance status |
| Annual_Premium       | Health insurance premium          |
| Policy_Sales_Channel | Sales acquisition channel         |
| Vintage              | Customer association duration     |
| Vehicle_Age          | Vehicle age category              |
| Vehicle_Damage       | Previous vehicle damage status    |

### Target

`Response`

* 1 → Interested in vehicle insurance
* 0 → Not interested in vehicle insurance

---

# 🤖 Machine Learning Pipeline

The training workflow consists of:

1. Data ingestion from MongoDB Atlas
2. Schema validation and integrity checks
3. Data preprocessing and feature transformation
4. Class imbalance handling using SMOTEENN
5. Model training using Random Forest
6. Model evaluation using F1 Score
7. Comparison with the currently deployed model
8. Promotion of the model if performance improves
9. Storage of production model in AWS S3

The production model is updated only when the new model outperforms the existing model according to the configured evaluation criteria.

---

# 🚀 CI/CD Workflow

Every push to the `main` branch triggers an automated deployment pipeline.

### Build Stage

* Configure AWS credentials
* Build Docker image
* Push image to Amazon ECR

### Deployment Stage

* Pull latest image on EC2
* Stop existing container
* Deploy updated container
* Start application

```text
GitHub Push
      │
      ▼
GitHub Actions
      │
      ▼
Amazon ECR
      │
      ▼
AWS EC2
      │
      ▼
FastAPI Application
```

---

# 📂 Project Structure

```text
src/
├── components
├── pipeline
├── cloud_storage
├── configuration
├── utils
└── entity

config/
templates/
static/
.github/workflows/

app.py
demo.py
Dockerfile
requirements.txt
```

---

# 🚀 Getting Started

## Clone Repository

```bash
git clone https://github.com/gaurxng12/MLOPS-project.git

cd MLOPS-project
```

## Create Environment

```bash
conda create -n vehicle python=3.10 -y

conda activate vehicle
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Configure Credentials

Configure your MongoDB Atlas and AWS credentials through environment variables before running the project.

## Run Training Pipeline

```bash
python demo.py
```

## Run Application

```bash
python app.py
```

Open:

```text
http://localhost:5000
```

---

# 🌐 API Endpoints

| Method | Endpoint | Description                                                                                                 |
| ------ | -------- | ----------------------------------------------------------------------------------------------------------- |
| GET    | `/`      | Renders the prediction form UI                                                                              |
| POST   | `/`      | Accepts customer details and returns a vehicle insurance prediction                                         |
| GET    | `/train` | Triggers the complete end-to-end training pipeline and updates the production model if performance improves |

---

# 📈 Roadmap

* MLflow integration
* Data drift monitoring
* Model performance dashboard
* Automated testing
* Hyperparameter optimization
* Workflow orchestration using Airflow or Prefect

---

# 📄 License

This project is licensed under the MIT License.
