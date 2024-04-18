---

# Dockerfile for Jenkins Server with Tools

This Dockerfile creates a Jenkins server with pre-installed tools such as kubectl, git, Docker CLI, and Terraform. It provides a convenient environment for continuous integration and deployment workflows.

## Usage

### Building the Docker Image

To build the Docker image, run the following command in the directory containing the Dockerfile:

```
docker build -t jenkins-with-tools .
```

### Running the Jenkins Server Container

To run the Jenkins server container on **Windows**, use the following command:

```
docker run `
--name jenkins `
--restart=on-failure `
--detach `
--env DOCKER_HOST=tcp://docker:2376 `
--env DOCKER_CERT_PATH=/certs/client `
--env DOCKER_TLS_VERIFY=1 `
--publish 80:8080 `
--volume $HOME/Desktop/Jenkins-Home:/var/jenkins_home `
--volume jenkins-docker-certs:/certs/client:ro `
jenkins-with-tools
```

### Running the Jenkins Server Container

To run the Jenkins server container on **Linux**, use the following command:

```
docker run `
--name jenkins `
--restart=on-failure `
--detach `
--env DOCKER_HOST=tcp://docker:2376 `
--env DOCKER_CERT_PATH=/certs/client `
--env DOCKER_TLS_VERIFY=1 `
--publish 80:8080 `
--volume jenkins-data:/var/jenkins_home `
--volume jenkins-docker-certs:/certs/client:ro `
jenkins-with-tools
```

This command will start the Jenkins server container in detached mode, exposing ports 80 for accessing the Jenkins web interface and port 50000 for Jenkins agent communication.

### Accessing Jenkins

Once the container is running, you can access the Jenkins web interface by navigating to [http://localhost:80](http://localhost:80) in your web browser. Follow the on-screen instructions to complete the setup.

Use this below command to access 'initialAdminPassword'
```
docker exec jenkins  cat /var/jenkins_home/secrets/initialAdminPassword
```

### Windows Execution

For Windows users, make sure you have Docker Desktop installed and running. You can then execute the provided commands in either PowerShell or Command Prompt.

### Linux Execution

For Linux users, ensure Docker is installed and running on your system. You can execute the provided commands in your terminal.

## Installed Tools

- **kubectl**: Command-line tool for interacting with Kubernetes clusters.
- **git**: Distributed version control system for tracking changes in source code during software development.
- **Docker CLI**: Command-line interface for Docker Engine, allowing you to build, manage, and deploy Docker containers.
- **Terraform**: Infrastructure as Code tool for building, changing, and versioning infrastructure safely and efficiently.

---
