# Jenkins Pipeline README

This Jenkins pipeline script automates the building, testing, and deployment process for a Java Maven application using Docker and Kubernetes. 

## Prerequisites

- Jenkins server installed and configured.
- Jenkins plugins installed: Pipeline, Credentials Binding, Docker Pipeline, Kubernetes CLI.
- Docker installed on Jenkins server.
- Access to an AWS account for pushing Docker images to Amazon ECR.
- Access to a Github repository for version control.

## Usage

1. **Set Up Jenkins Credentials**

   - Create credentials for Docker registry (`ecr-credentials`), AWS access (`jenkins_aws_access_key_id` and `jenkins_aws_secret_access_key`), and Github(`github-credentials`).

2. **Configure Jenkins Pipeline**

   - Create a new Jenkins pipeline job.
   - Copy and paste the provided pipeline script into the pipeline script section.
   - Save the configuration.

3. **Configure Kubernetes Cluster**

   - Ensure that you have a Kubernetes cluster configured and accessible to Jenkins.

4. **Run the Pipeline**

   - Trigger the pipeline manually or set up a webhook for automatic triggers on code changes.
   - The pipeline consists of the following stages:
     - **Increment Version**: Increments the version of the application.
     - **Build App**: Builds the Java Maven application.
     - **Build Image**: Builds the Docker image and pushes it to Amazon ECR.
     - **Deploy**: Deploys the Docker image to Kubernetes.
     - **Commit Version Update**: Commits the version update to Github repository.

5. **Monitor the Pipeline**

   - Monitor the progress of the pipeline in the Jenkins interface.
   - Check logs for each stage to ensure successful execution.

## Environment Variables

- `ECR_REPO_URL`: URL of the Amazon ECR repository.
- `IMAGE_REPO`: Docker image repository URL.
- `AWS_ACCESS_KEY_ID`: AWS access key ID.
- `AWS_SECRET_ACCESS_KEY`: AWS secret access key.
- `APP_NAME`: Name of the Java Maven application.
- `USER`: Username for accessing Docker registry and Github.
- `PASS`: Password for accessing Docker registry and Github.

