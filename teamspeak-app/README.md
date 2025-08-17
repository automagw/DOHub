# TeamSpeak Application

This project contains a containerized TeamSpeak application that can be deployed to a Digital Ocean Kubernetes cluster.

## Project Structure

```
teamspeak-app
├── src
│   └── entrypoint.sh
├── Dockerfile
├── k8s
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
├── .dockerignore
└── README.md
```

## Prerequisites

- Docker installed on your local machine.
- Access to a Digital Ocean account with a Kubernetes cluster set up.
- `kubectl` installed and configured to interact with your Digital Ocean Kubernetes cluster.

## Building the Docker Image

To build the Docker image for the TeamSpeak application, navigate to the project directory and run the following command:

```bash
docker build -t teamspeak-app .
```

## Running the Docker Container Locally

To run the Docker container locally for testing, use the following command:

```bash
docker run -d -p 9987:9987 -p 30033:30033 -p 10011:10011 teamspeak-app
```

## Deploying to Digital Ocean Kubernetes

1. **Apply the Kubernetes Deployment:**

   Run the following command to create the deployment in your Kubernetes cluster:

   ```bash
   kubectl apply -f k8s/deployment.yaml
   ```

2. **Create the Service:**

   Next, create the service to expose the TeamSpeak application:

   ```bash
   kubectl apply -f k8s/service.yaml
   ```

3. **Set Up Ingress (Optional):**

   If you want to set up ingress for your application, apply the ingress configuration:

   ```bash
   kubectl apply -f k8s/ingress.yaml
   ```

## Accessing the TeamSpeak Server

Once the application is deployed, you can access the TeamSpeak server using the appropriate IP address and ports specified in your service configuration.

## Additional Information

For further customization, refer to the individual files in the `k8s` directory for deployment, service, and ingress configurations. Adjust the `entrypoint.sh` script as needed to configure the TeamSpeak server settings.