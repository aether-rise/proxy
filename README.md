
# Proxy Router

This repository contains the Docker image for running the Proxy Router, which can be used for Morpheus Lumerin-related deployments. Below are basic instructions for running the image directly and for using the provided Docker Compose setup.

## Running the Docker Image Directly

You can run the Proxy Router image directly using the following command. Replace placeholders with your private key and Alchemy app key.

```bash
docker run -d \
  -e WALLET_PRIVATE_KEY=[yourprivatekey] \
  -e OPENAI_BASE_URL=http://ollama:11434/v1 \
  -e ETH_NODE_ADDRESS=wss://arb-sepolia.g.alchemy.com/v2/[your_alchemy_app_key] \
  -e EXPLORER_API_URL="https://api-sepolia.arbiscan.io/api" \
  -p 8080:8080 \
  -p 8082:8082 \
  -p 3333:3333 \
  -v $(pwd)/logs:/app/logs \
  -v ~/go/pkg/mod:/go/pkg/mod \
  ghcr.io/aether-rise/proxy:latest
```

This command will start a container using the Proxy Router image and expose the required ports. Make sure to provide your own `WALLET_PRIVATE_KEY` and `ETH_NODE_ADDRESS`.

## Running with Docker Compose

This repository includes a `docker-compose.yml` file for setting up the Proxy Router and its dependencies. To use Docker Compose:

1. Replace `[yourprivatekey]` and `[your_alchemy_app_key]` in the environment variables with your actual private key and Alchemy app key.

2. Start the services with:

   ```bash
   docker-compose up -d
   ```

This will start both the `proxy-router` and `ollama` services, exposing the necessary ports. Logs will be stored in the `./proxy-router/logs` directory, and the setup will use GPU resources for the `ollama` container if available.

### Stopping Services

To stop the services, run:

```bash
docker-compose down
```

This command will stop and remove the containers but will preserve the volumes.

## License

This project is licensed under the terms of the MIT license.
