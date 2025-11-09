# DevOps Task 1: Automated Code Deployment using GitHub Actions

### Objective
The objective of this task was to build a complete CI/CD pipeline to automate the deployment of a simple Node.js web application. This was achieved by containerizing the application using **Docker** and then setting up an automated workflow with **GitHub Actions** to build and push the Docker image to a registry.

### Tools Used
* **GitHub**: For version control and hosting the repository.
* **GitHub Actions**: The CI/CD platform used to automate the workflow.
* **Node.js**: The technology used to build the sample web application.
* **Docker**: Used to create a portable container image of the application.
* **Docker Hub**: The container registry where the final Docker image is stored.

### Project Files Explained
This repository contains all the necessary files to complete the task:

- **`index.js`**: This file contains the core logic for the Node.js application. It uses the Express framework to create a simple web server that listens on port 3000 and responds with "Hello from the Node.js Demo App!" when a user visits the root URL.
- **`package.json`**: This file manages the Node.js project's dependencies and scripts. It defines the `start` command used to run the application (`node index.js`) and lists `express` as a required dependency.
- **`Dockerfile`**: This is a key part of the project. It provides a set of instructions for Docker to build a container image. It specifies a base Node.js image, sets up the working directory, installs dependencies, and defines the command to run the application within the container.
- **`.github/workflows/main.yml`**: This is the configuration file for the CI/CD pipeline. It defines the automated steps that GitHub Actions will follow to test, build, and deploy the application.

---

### The CI/CD Pipeline
The workflow in `main.yml` is triggered automatically on every **push to the `main` branch**. It contains a single job named `build-and-push`, which performs the following steps in sequence:

1.  **Checkout repository**: This step uses a GitHub Action to copy the code from the repository onto the runner, making it available for the subsequent steps.
2.  **Log in to Docker Hub**: This step securely logs in to Docker Hub using the credentials stored in the repository's GitHub Secrets. This is a crucial step for authentication before pushing the image.
3.  **Build Docker image**: This step uses the `Dockerfile` to build the application's container image. It tags the image with the Docker Hub username and repository name.
4.  **Push Docker image**: This final step pushes the newly built image to Docker Hub, making it available for use and future deployment.

### Security with GitHub Secrets
To protect sensitive information like your Docker Hub username and access token, we used **GitHub Secrets**. Instead of hardcoding credentials directly into the `main.yml` file, we stored them as encrypted variables in the repository settings. The pipeline can then securely access these values at runtime without ever exposing them in the code or logs.

---

### Deliverables
The successful completion of this task is demonstrated by the following deliverables:
-   A public GitHub repository containing all project files.
-   A working CI/CD pipeline in GitHub Actions that automatically builds and pushes the Docker image to Docker Hub on every push to the `main` branch.
-   This detailed `README.md` file explaining the project's setup and functionality.
