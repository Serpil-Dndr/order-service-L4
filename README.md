# Order Service

The Order Service is a backend service that receives orders from the store-front and sends these orders to a RabbitMQ message queue. It enables decoupling of the order processing logic from the product service, allowing for more scalable and maintainable architecture.

## Requirements

- Node.js
- npm
- RabbitMQ

## Setup Instructions
1. Update the package list:
   ```bash
   sudo apt update
2. Install the NodeSource repository for Node.js 20: First, download and add the NodeSource repository for Node.js 20.x.
   ```bash
   curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
3. Install Node.js and npm
   ```bash
   sudo apt update
   sudo apt install -y nodejs
4. Navigate to the `order-service` directory:
   ```bash
   cd order-service
5. Install dependencies:

   The service depends on several npm packages (such as express for the web server and amqplib for RabbitMQ communication). Install these dependencies using npm:

   ```bash
   npm install
6. Run the service:
   
   Once all dependencies are installed, start the service:

   ```bash
   node index.js 
The service will be running on http://localhost:3000.

## Testing
1. Before the service can send orders to RabbitMQ, make sure RabbitMQ is installed and running locally. If not, follow the setup instructions in the RabbitMQ documentation provided earlier.
2. Install the REST Client extension in VS Code to use .http files.
3. Use the provided test-order-service.http file to test the service.

### Docker Setup 

1. Create Dockerfile


2. Build Docker image: 
   command:docker build -t <image_name> .
   docker build -t <image_name> . –no-cache

```bash
docker build -t order-service:latest . 
```

3. Run a Docker container from order-service:latest image and expose it on port 3000:

   ```bash
   docker run --rm -d -p 3000:3000 order-service:latest
   ```

4. List Local images:

   ```bash 
   docker images
   ```

5. If you would like to delete image you can delete from docker hub manuallly or use this command 
 
   ```bash
   docker rmi <image_name>
   ```

6. Pull an Image from Docker Hub:

   ```bash
   docker pull <image_name>
   ```

7. You can run each directory induvally or yo can do it docker compose following command, but dont do it specific file make it inside the parent folder(root directory). Add docker-compose.yml 
file. Add yml file.  it will be same level with order-service, product service so on...

8. Run the application using Docker Compose

   ```bash 
   docker-compose up --build
   ```
### This will build and run all the services together. You should be able to access the store-front at http://localhost:80.

9. Before pushing the docker image login to the docker hub 

      ```bash
      docker login
      ```
10. Tag the images:

```bash
docker tag order-service:latest serpild/order-service:latest
docker tag product-service:latest serpild/product-service:latest
docker tag store-front:latest serpild/store-front:latest
```

11. Push the images:

```bash
docker push serpild/order-service:latest
docker push serpild/product-service:latest
docker push serpild/store-front:latest
```

12. Clean up environment 

```bash 
docker system prune -a
```







 
