## Setup ##
First, complete the basic Rust setup instructions. If you want to play at the code level.

If No, then plz follow this simple guide to make your life easy :)

Run in Docker

# Install Docker & Docker-Compose

First, install Docker and Docker Compose. Follow the basic installation guide [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)

For a Windows Machine

[Follow the guide mentioned here](https://docs.docker.com/desktop/windows/install/)

Installation from the terminal on a Ubuntu/Linux Machine 

`curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

`chmod +x /usr/local/bin/docker-compose`

# Docker quick guide

To check the compose version
```bash
docker-compose --version
```
To run the build

```bash
docker-compose up --build -d
``` 

To stop the service

```bash
docker-compose down
```

To view the installed images locally

```bash
docker images
```

To delete the images

```bash
docker rmi <IMAGE ID>
```

To get more idea about the project and the build please refer the link [Project Brief](https://github.com/WowLabz/tasking_backend#readme)

# Guide To Run All The Services At Once

Clone the repo [Dot_Marketplace_Docker](https://github.com/WowLabz/dot_marketplace_docker.git)

Once this repo is cloned, follow the commands below to start all the services at once from the main project directory

```bash
docker-compose up --build -d
```
You will be able to see all the running services using 
```bash
docker ps
```
Each of these services will be running on the local system ports as below
1. dot_marketplace_frontend: Directly run the frontend to test out the application. [http://127.0.0.1:9001]
2. authentication_service: This is the api server to check the authentication service [http://127.0.0.1:7001]
3. marketplace_mongo: Mongodb for the application
4. dot_marketplace_node: Substrate based blockchain node, this can also be tested on the [polkadot js explorer](https://polkadot.js.org/apps/#/) Select local node to connect to the local running chain.[ws://127.0.0.1:9944]

To stop all the services
```bash
docker-compose down
```

# Guide To Run Each Of The Services Individually

Names of the individual service files
1. Blockchain Node: `tasking_backend.docker-compose.yml`
2. UI: `tasking_frontend.docker-compose.yml`
3. Auth Server: `authentication_service.docker-compose.yml`
4. Mongodb: `marketplace_mongo.docker-compose.yml`

To run the services individually 

```bash
docker-compose -f <file_name> up --build -d
```
To stop an individual service

```bash
docker-compose -f <file_name> down
```
# Individual Service Repos (To do a code walkthrough)
1. [Tasking Backend Node](https://github.com/WowLabz/tasking_backend.git)
2. [Tasking Frontend](https://github.com/WowLabz/tasking_frontend.git)
3. [Authentication Service](https://github.com/WowLabz/authentication_service.git)

# Container Instructions
In order to check for the status of the running node run 
```bash
docker-compose logs <CONTAINER ID>
```

# Run UI
You can access the frontend application on `http://127.0.0.1:9001`

![Screenshot_15](https://user-images.githubusercontent.com/11945179/131972401-6a700ce1-d938-45e2-931d-a50986daac12.png)

# Launch Interactive Bash Session with the Node
    
```bash
docker exec -it <CONTAINER ID> bash
``` 
|OR| 
```bash
docker exec -it <CONTAINER ID> /bin/sh
```
    
# Run Tests for the blockchain node

Enter into the interactive bash with the container id pertaining to dot_marketplace_node and run the following commands
    
`cargo test` (This will run all the test cases)
 
 `cargo test <test_name>` (For checking any specific test case)
 
 # Run Tests for the authentication service

Enter into the interactive bash with the container id pertaining to authentication service and run the following commands

Note: Run the tests using a single thread
```bash
cargo test -- --test-threads=1
```
# Interacting with Polkadot Js Apps Explorer
    
![BlocksFinality](https://user-images.githubusercontent.com/11945179/131971129-d166e10f-5efe-4d1a-8fab-082ba8a13a07.png)
    
To check the working of palletTasking go to Developers -> Extrinsics -> Submit the following Extrinsic -> palletTasking -> createTask (Starting Point, explore further we have worked on the full tasking lifecycle) 

![ChainExtrinsics](https://user-images.githubusercontent.com/11945179/131971070-580769be-7827-429e-8d9b-7216997813ca.png)
    
    
To read about the working of the pallet please refer the guide [Description](https://github.com/WowLabz/tasking_backend/tree/dev#readme)

## Chat App workflow on Polkadot.js explorer 

>Video  walkthrough

https://user-images.githubusercontent.com/58659064/158811706-868510e4-dfdd-42d0-8d2e-9620a59e141c.mp4

>Write a Message

![image](https://user-images.githubusercontent.com/58659064/158810705-9836728f-68fa-4256-87ba-ce4d8c19cde9.png)

>Reply to a Message

![image (1)](https://user-images.githubusercontent.com/58659064/158810748-30252898-42e6-48de-bab1-efb201864459.png)

>Message in storage

![image (2)](https://user-images.githubusercontent.com/58659064/158811293-732f066e-77fb-4629-893f-78a9e7ceddcc.png)

>Mark a message as read

![image (3)](https://user-images.githubusercontent.com/58659064/158811312-119b41db-5504-4d3e-b3b0-31ff57640329.png)












