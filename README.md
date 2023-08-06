# GitHub Workflows for Golang Projects

This repository provides a GitHub Workflow that automates the process of building and deploying a Golang Microservice using Planton Cloud.

The workflow performs the following steps:

1. **Checkout Code:** Fetches the codebase of your application from the repository.

2. **Install Planton CLI:** Installs the Planton Command Line Interface (CLI), which is a crucial tool used in subsequent steps.

3. **Verify Planton CLI Installation:** Checks the installed Planton CLI version to verify the successful installation.

4. **Login to Planton Cloud:** Uses your provided Planton Cloud credentials to authenticate your session.

5. **Setup Golang:** Configures the Golang environment necessary for building the application. Uses version '1.20.0'.

6. **Setup Git SSH:** Sets up Git SSH keys using your provided Artifact Store ID on Planton Cloud, to authenticate to your Git server.

7. **Build with Make:** Executes the Make build for your application.

8. **Build & Push Docker Image:** Builds a Docker image from your application and pushes it to the specified Docker repository.

9. **Deploy Microservice:** Deploys the built Microservice to an environment on Planton Cloud.

## Usage

To make use of this workflow, you need to include it in your GitHub Actions. The workflow can be triggered on a `workflow_call`.

```yaml
on:
  workflow_call:
```

### Secrets and Inputs

The workflow requires the following secrets and inputs that need to be passed when calling the workflow:

#### Secrets

- `PLANTON_CLOUD_CLIENT_ID`: Your Planton Cloud Client ID
- `PLANTON_CLOUD_CLIENT_SECRET`: Your Planton Cloud Client Secret

#### Inputs

- `PLANTON_CLOUD_ARTIFACT_STORE_ID`: The ID of the Artifact Store on Planton Cloud
- `DOCKER_REPO_HOSTNAME`: The hostname of the Docker repository in the Artifact Store
- `CONTAINER_IMAGE_REPO`: The repository of the Docker image to be built and pushed
- `CONTAINER_IMAGE_TAG`: The tag of the Docker image to be built and pushed
- `PLANTON_CLOUD_ENVIRONMENT_ID`: The ID of the target environment on Planton Cloud
- `PLANTON_CLOUD_ENVIRONMENT_NAME`: The name of the target environment on Planton Cloud
- `PLANTON_CLOUD_MICROSERVICE_INSTANCE_VERSION`: The version of the Microservice Instance (i.e., 'main' or 'review-<pull-request-number>')

## Contributing

If you have suggestions for how this GitHub Action could be improved, or want to report a bug, open an issue! We'd love all and any contributions.

## License

This project is licensed under the [MIT License](LICENSE).
