# 200 - 2. Write Docker file(s)

You need a Dockerfile for each custom image you want to build; you also need a **Dockerfile** for each container to be deployed, whether you deploy automatically from your IDE or manually using the Docker CLI (```docker run``` and ```docker-compose``` commands). 

- If your application contains a single custom service, you need a single Dockerfile. 
- If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.

The Dockerfile is placed in the ```root / containers / app / service``` folder of your application or service. It contains the commands that tell Docker how to set up and run your application or service in a container. You can manually create a Dockerfile in code and add it to your project along with your dependencies.


