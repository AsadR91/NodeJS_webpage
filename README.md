# 🐳 Node.js Webpage in Docker

This guide shows you how to clone a simple Node.js web project, build a Docker image from it, and run the app in a container.

## 📦 Clone the Repository

Start by downloading the project from GitHub:

```bash
git clone https://github.com/AsadR91/NodeJS_webpage.git
cd NodeJS_webpage/
```

## 🧾 Project Files

List the files in the folder:

```
ls
```
You should see files like:

app.js

package.json

Dockerfile (you can use this or create your own)

## 🐳 Dockerfile (Optional)
If a Dockerfile doesn’t already exist, create one with the following content:

```
FROM node:18

# Set working directory inside the container
WORKDIR /app

# Copy app files
COPY . .

# Install dependencies
RUN npm install

# Expose the port the app listens on
EXPOSE 8081

# Run the app
CMD ["node", "app.js"]
```

## 🛠️ Build the Docker Image
Use the docker build command to create an image:


```
docker build -t devdocker91/nodejs:latest .
```
-t assigns a name and tag to the image.

. tells Docker to use the current directory.

## 📷 List Docker Images
To confirm your image was created:
```
docker images

```
Look for devdocker91/nodejs in the list.

## 🚀 Run the Container
Now start the app in a Docker container:

```
docker run -d -p 8082:8081 devdocker91/nodejs

```

-d runs in the background (detached mode).

-p 8082:8081 maps port 8082 on your machine to port 8081 inside the container.

Now visit:
👉 http://localhost:8082

You should see the Node.js webpage!

## 🧼 Clean Up
To stop and remove the container:

```
docker ps           # Get the container ID
docker stop <id>
docker rm <id>
```
To remove the image:

```
docker rmi devdocker91/nodejs
```

## 🐙 Bonus: Push to Docker Hub

If you want to share this image:

Log in:

```
docker login
```

Push the image:

```
docker push devdocker91/nodejs:latest
```

Make sure the repository exists on Docker Hub first.

### Note: You will have to create the DockerHub account and create the repository with the exact name.







