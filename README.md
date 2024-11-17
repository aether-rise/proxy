
# Proxy Router

This repository contains the Docker image for running the Proxy Router. Below are basic instructions for using the provided Docker Compose setup.

This command will start a container using the Proxy Router image and expose the required ports. Make sure to provide your own `WALLET_PRIVATE_KEY` and `ETH_NODE_ADDRESS`.

## Running with Docker Compose

This repository includes a `docker-compose.yml` file for setting up the Proxy Router and its dependencies. To use Docker Compose:

1. Replace `[yourprivatekey]` and `[your_alchemy_app_key]` in the environment variables with your actual private key and Alchemy app key.

2. Start the services with:

   ```bash
   docker-compose up -d
   ```

This will start both the `proxy-router` and `ollama` services, exposing the necessary ports. The setup will use GPU resources for the `ollama` container if available.

### Stopping Services

To stop the services, run:

```bash
docker-compose down
```

This command will stop and remove the containers but will preserve the volumes.

## License

This project is licensed under the terms of the MIT license.
