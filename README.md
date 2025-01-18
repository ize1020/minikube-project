# My Website Repo

This repository contains:
- A `Jenkinsfile` to automate the CI/CD pipeline for website deployment.
- Kubernetes YAML manifests to deploy the website.
- Website source files located in the `src/` directory.

### Steps to Deploy
1. Push this repository to GitHub.
2. Configure a Jenkins pipeline with "Pipeline script from SCM."
3. Run the pipeline to deploy the website.
4. Access the website via NodePort at `http://<minikube-ip>:30080`.

### Files
- **Jenkinsfile**: Defines the Jenkins pipeline.
- **website-deployment.yaml**: Kubernetes manifests.
- **src/index.html**: The website content.
