# SIT323-2025-Prac5D: Dockerized Calculator Microservice

This project demonstrates how to Dockerize and publish a Node.js-based calculator microservice to **Google Cloud Artifact Registry**, following production-ready practices.

---

## Project Overview

- **Language:** Node.js  
- **Containerization Tool:** Docker  
- **Cloud Provider:** Google Cloud Platform (GCP)  
- **Region Used:** `australia-southeast1`  
- **Registry Used:** Artifact Registry (NOT GCR due to Deakin policy)

---

## Folder Structure

```
sit323-2025-prac5d/
│
index.js              # Main microservice file
package.json          # Node.js dependencies
Dockerfile            # Docker build configuration
README.md             # This file
```

---

## Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Google Cloud CLI (gcloud)](https://cloud.google.com/sdk/docs/install)
- Access to Google Cloud Project: `sit323-25t1-ling-109f166`

---

## Deployment Steps

### Step 1: Authenticate with Google Cloud

```bash
gcloud auth login
gcloud config set project sit323-25t1-ling-109f166
gcloud auth configure-docker australia-southeast1-docker.pkg.dev
```

---

### Step 2: Create Artifact Registry

```bash
gcloud artifacts repositories create calculator-repo \
  --repository-format=docker \
  --location=australia-southeast1 \
  --description="Docker repo for SIT323 Task 5.2D"
```

> Only needed the first time.

---

### Step 3: Build the Docker Image

```bash
docker build -t australia-southeast1-docker.pkg.dev/sit323-25t1-ling-109f166/calculator-repo/calculator:v1 .
```

---

### Step 4: Push the Image to Google Artifact Registry

```bash
docker push australia-southeast1-docker.pkg.dev/sit323-25t1-ling-109f166/calculator-repo/calculator:v1
```

You should see confirmation in your terminal and the image in GCP → Artifact Registry.

---

### Step 5: Run the Container Locally for Testing

```bash
docker run -p 3000:3000 australia-southeast1-docker.pkg.dev/sit323-25t1-ling-109f166/calculator-repo/calculator:v1
```

Then visit `http://localhost:3000` in your browser to confirm it's working.

---

## Final Result

Image successfully published to:

```
australia-southeast1-docker.pkg.dev/sit323-25t1-ling-109f166/calculator-repo/calculator:v1
```

Source code pushed to GitHub:

[https://github.com/LingJiRong/sit323-2025-prac5d](https://github.com/LingJiRong/sit323-2025-prac5d)

---

## Author

**Ling Ji Rong**  
S223521365  
SIT323 – Cloud-Native Application Development  
Deakin University

---
