# Dockerized Nginx Web Server

This project sets up a basic web server using Nginx in a Docker container. Follow these steps to build and run the environment, which serves a custom HTML page using Nginx.

## Prerequisites
- Docker installed on your machine. ([Docker Installation Guide](https://docs.docker.com/get-docker/))

## Setup Instructions

### Step 1: Project Setup

1. **Create a Project Directory**:
   - Open a terminal and create a new directory for the project files:

     ```bash
     mkdir nginx-docker-setup
     cd nginx-docker-setup
     ```

2. **Create a Dockerfile**:
   - In the project directory, create a `Dockerfile`:

     ```bash
     touch Dockerfile
     ```

3. **Define the Dockerfile**:
   - Open the Dockerfile in a text editor and add the following configuration to set up an Nginx server:

     ```Dockerfile
     # Use the official Nginx image from Docker Hub
     FROM nginx:latest

     # Copy a custom HTML file to serve as the index page
     COPY index.html /usr/share/nginx/html/index.html

     # Expose port 80 to the host
     EXPOSE 80
     ```

4. **Create a Custom HTML File**:
   - Create a file named `index.html` in the project directory. This file will be served by the Nginx web server:
    
     ```html
     <html>
       <head>
         <title>Welcome to Dockerized Nginx!</title>
       </head>
       <body>
         <h1>Hello from Nginx running in a Docker container!</h1>
       </body>
     </html>
     ```

### Step 2: Build and Run the Docker Container

1. **Build the Docker Image**:
   - In the project directory, run the following command to build the Docker image:
     
     ```bash
     docker build -t nginx-docker .
     ```

2. **Run the Docker Container**:
   - Start the container, mapping port 80 of the container to port 8080 on your host machine:

     ```bash
     docker run -d -p 8080:80 nginx-docker
     ```

3. **Access the Web Server**:
   - Open a web browser and navigate to `(http://52.35.121.164:8080/)`. You should see the message from `index.html` displayed, confirming that the Nginx server is running correctly in the Docker container.

### Step 3: Push to GitHub

1. **Initialize a Git Repository**:
   - If you haven't already, initialize a Git repository in the project directory:

     ```bash
     git init
     ```

2. **Commit and Push the Files to GitHub**:
   - Add the files, commit them, and push to your GitHub repository:

     ```bash
     git add .
     git commit -m "Initial commit - Dockerized Nginx Web Server"
     git remote add origin https://github.com/pavan5779/Task-2_Cloud_Ambassidor.git
     git push -u origin main
     ```

## Files in This Repository

- `Dockerfile`: Defines the Nginx Docker container setup.
- `index.html`: A simple HTML file served by Nginx.
- `README.md`: Documentation on setup and usage.

## Notes

- Make sure Docker is installed and running on your machine before building the image.
- Modify the `index.html` file as needed to serve different content.
- To stop the container, run:

  ```bash
  docker ps   # Find the container ID
  docker stop <container-id>
