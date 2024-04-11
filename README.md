# Jenkins Pipeline README

## Description
This Jenkins Pipeline script defines a multi-stage build and deployment process for an application. It uses Groovy syntax and is designed to run in a Jenkins environment.

## Prerequisites
- Jenkins installed and configured
- Jenkins plugins:
  - Pipeline
  - Kubernetes
- Docker installed on Jenkins agent(s)

## Pipeline Overview
This pipeline consists of three stages:

1. **Build app**: This stage builds the application.
2. **Build image**: This stage builds a Docker image for the application.
3. **Deploy**: This stage deploys the Docker image to a Kubernetes cluster.

## Usage
1. Configure Jenkins credentials:
   - `jenkins_aws_access_key_id`: AWS access key ID for deployment.
   - `jenkins_aws_secret_access_key`: AWS secret access key for deployment.

2. Create a Jenkins Pipeline job and configure it to use this script.

3. Run the Pipeline job. The job will execute the following steps:
   - Build the application.
   - Build the Docker image.
   - Deploy the Docker image to a Kubernetes cluster using `kubectl`.

## Script Explanation
- The `pipeline` directive defines the entire Jenkins Pipeline.
- `agent any` specifies that the pipeline can execute on any available agent.
- `stages` block defines individual stages of the pipeline.
  - Each `stage` represents a specific phase of the pipeline process.
  - Inside each `stage`, `steps` block contains the actions to be performed.
- The `script` block allows the execution of Groovy code within the pipeline.
- Environment variables (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`) are used to store AWS credentials securely.

## Notes
- This script assumes that Docker and Kubernetes are set up and configured on the Jenkins environment.
- Adjust the deployment command (`kubectl create deployment`) in the `deploy` stage according to your Kubernetes setup and requirements.

For more information on Jenkins Pipeline syntax and usage, refer to the [official documentation](https://www.jenkins.io/doc/book/pipeline/).