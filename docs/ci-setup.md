# 📘 DevOps CI/CD Setup Documentation (Phase 1)

## 👤 Author

Sumit Raj

---

# 🎯 Objective

To build a **CI/CD pipeline using GitHub Actions** with:

* Self-hosted runner
* Basic workflow execution
* Understanding pipeline fundamentals

---

# 🧠 High-Level Goal

Create a system where:

* Code push → triggers pipeline
* Pipeline runs on your machine
* Executes steps automatically

---

# 🏗️ Architecture (Current Phase)

Developer → GitHub Repo → GitHub Actions → Self-hosted Runner (Local Machine)

---

# 🧱 Step-by-Step Implementation

## 🔹 Step 1: GitHub Organization Creation

### What we did:

* Created an organization: `devops-lab-sumit`

### Why:

* Simulates real company environment
* Better management of repos, pipelines, and permissions

---

## 🔹 Step 2: Repository Creation

### Repo:

`devops-pipeline`

### Why:

* Central place for:

  * CI/CD workflows
  * Terraform (later)
  * Application code (later)

---

## 🔹 Step 3: Self-Hosted Runner Setup

### 📁 Created Directory

```powershell
mkdir actions-runner
cd actions-runner
```

### Why:

* Dedicated location for runner files

---

### 📥 Download Runner

```powershell
Invoke-WebRequest -Uri <github-runner-url> -OutFile actions-runner-win-x64-2.333.1.zip
```

### Why:

* Downloads GitHub runner software

---

### 📦 Extract Runner

```powershell
Expand-Archive -Path actions-runner-win-x64-2.333.1.zip -DestinationPath .
```

### Why:

* Extracts runner executable files

---

### ⚙️ Configure Runner

```powershell
.\config.cmd --url https://github.com/devops-lab-sumit/devops-pipeline --token <token>
```

### What happened:

* Machine registered as runner
* Connected to GitHub

---

### ▶️ Start Runner

```powershell
.\run.cmd
```

### Output:

```
Listening for Jobs
```

### Why:

* Runner starts listening for pipeline jobs

---

# ⚠️ Important Learning

* Runner is a **machine that executes jobs**
* It can be:

  * Local laptop
  * EC2 instance (later)

---

# 🔹 Step 4: First CI Pipeline Creation

### File Created:

```
.github/workflows/ci.yml
```

---

## 📜 Workflow Code (Current)

```yaml
name: CI Pipeline

on:
  push:

jobs:
  build:
    runs-on: self-hosted

    steps:
      - name: Say Hello
        run: echo "Hello from my self-hosted runner"
```

---

# 🧠 Explanation of Key Concepts

## 🔹 name

* Defines workflow name

## 🔹 on: push

* Trigger when code is pushed

## 🔹 jobs

* Group of tasks

## 🔹 runs-on: self-hosted

* Uses your local runner

## 🔹 steps

* List of commands

## 🔹 run

* Executes shell command

---

# 🧪 Result

Pipeline successfully executed:

Output:

```
Hello from my self-hosted runner
```

---

# 🎯 What We Achieved

✅ Working CI pipeline
✅ Self-hosted runner integration
✅ Automatic trigger on push
✅ Basic command execution

---

# 🚀 What We Will Do Next

## 🔥 Phase 2 (Next Steps)

### CI Enhancements

* Checkout code
* Branch detection (feature vs release)
* Version/tag generation

---

### Docker Integration

* Build Docker image
* Tag image dynamically
* Push to registry

---

### Security (Simulated)

* Code scanning (mock)
* Image scanning (mock)

---

### AWS Integration

* OIDC authentication
* Push image to ECR

---

### CD Pipeline

* Deploy to EKS

---

### Terraform (Infra Pipeline)

* Create:

  * IAM roles
  * OIDC provider
  * ECR
  * EKS
* Manage state (S3 + DynamoDB)

---

# 🧠 Key Learnings So Far

* YAML structure and indentation
* GitHub Actions workflow basics
* Runner architecture
* CI trigger mechanism

---

# 📌 Future Architecture (Final Goal)

CI/CD + Infra as Code (Terraform) + AWS (EKS, ECR, IAM)

---
