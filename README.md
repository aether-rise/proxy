
# Proxy Router

This repository contains the Docker image for running the Proxy Router. Below are basic instructions for using the provided Docker Compose setup.

This command will start a container using the Proxy Router image and expose the required ports. Make sure to provide your own `WALLET_PRIVATE_KEY` and `ETH_NODE_ADDRESS`.


## Pre-requisites:
 - Linux host with Nvidia GPU
 - Nvidia drivers installed
 - git installed
 - Docker installed (with compose support)
 - Nvidia container toolkit installed
 - accessible from the Internet on port 3333 and SSH/22

## Running with Docker Compose

This repository includes a `docker-compose.yml` file for setting up the Proxy Router and its dependencies. To use Docker Compose:

1. Replace `[yourprivatekey]` and `[your_alchemy_app_key]` in the environment variables with your actual private key and Alchemy app key.

2. Start the services with:

    ```bash
    docker compose up -d
    ```
     - This will start both the `proxy-router` and `ollama` services, exposing the necessary ports. The setup will use GPU resources for the `ollama` container if available.

3. Verify proxy-router shows "started watching events, address 0x1234556..":
  
    ```bash
    docker compose logs
    ```

4. Verify proxy and llm instance are running by opening

    *** probably need to ssh tunnel to port 8082 from localhost (this shouldn't be exposed publicly), or alternatively update environment variables "WEB_* to point to your public ip/dns name for the server ***
    
    TODO: provide ssh tunnel instructions

    `http://localhost:8082/swagger/index.html#/chat/post_v1_chat_completions`
  
    - Click 'try it out'

    - Click 'execute'

      the response code should be 200 with a response from the llm. 


### Stopping Services

To stop the services, run:

```bash
docker-compose down
```

This command will stop and remove the containers but will preserve the volumes.

## License

This project is licensed under the terms of the MIT license.
