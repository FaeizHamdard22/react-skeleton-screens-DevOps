````md
React Skeleton Screens – DevOps CI/CD Deployment

This project is originally cloned from [MahdiAtlas2004/react-skeleton-screens](https://github.com/MahdiAtlas2004/react-skeleton-screens), then Dockerized and automated with Jenkins pipeline by [Faeiz Hamdard](https://github.com/FaeizHamdard22).

---

##  What Was Added

-  `Dockerfile` – Multi-stage Docker build for React + Nginx
-  `Jenkinsfile` – CI/CD pipeline for automated build & deploy

---

##  Repository

**This repo:**  
`https://github.com/FaeizHamdard22/react-skeleton-screens-DevOps`

---

## 🛠 Requirements

-  Docker
- ⚙ Jenkins
-  Git installed
-  Jenkins user in Docker group:
  ```bash
  sudo usermod -aG docker jenkins
  sudo systemctl restart jenkins
````

---

##  How to Run the Pipeline

### 1. Clone This Repo into Jenkins Project

In Jenkins > New Item:

* Type: **Pipeline**
* Name: `react-skeleton-devops`
* In Pipeline settings:

  * `Git URL`:

    ```
    https://github.com/FaeizHamdard22/react-skeleton-screens-DevOps.git
    ```
  * `Branch`: `main`

---

### 2. Jenkinsfile Overview

```groovy
pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/FaeizHamdard22/react-skeleton-screens-DevOps.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t react-skeleton-app .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run -d -p 8081:80 react-skeleton-app'
      }
    }
  }
}
```

---

##  Test the App

Once pipeline completes successfully, open your browser:

```text
http://YOUR_SERVER_IP:8081
```

If Jenkins is on public server → replace `YOUR_SERVER_IP` with actual IP or domain.

---

##  Manual Docker Build (Optional)

```bash
git clone https://github.com/FaeizHamdard22/react-skeleton-screens-DevOps.git
cd react-skeleton-screens-DevOps
docker build -t react-skeleton-app .
docker run -d -p 8081:80 react-skeleton-app
```

---

## Credits

Original frontend project by:
[MahdiAtlas2004](https://github.com/MahdiAtlas2004/react-skeleton-screens)

CI/CD & Docker setup by:
[Faeiz Hamdard](https://github.com/FaeizHamdard22)

---

