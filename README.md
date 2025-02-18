# Docker Tutorial
---
⚙️ **Docker**

**Application Tech Stack:** It represents technologies used in the application, helping developers build, test, and deploy software efficiently across different environments. A solid tech stack ensures smooth functionality and scalability.

1. 🌟 **Frontend Stack:** HTML, CSS, JS, BS & Angular / React JS - These technologies shape the visible part of any application, ensuring user interaction and dynamic experiences.
2. 💻 **Backend Stack:** Java / .Net / Python / Node JS - The backbone of application logic, managing data processing, user authentication, and server communications.
3. 🏛️ **Database:** Oracle / MySQL / PostgresSQL / Mongo DB - Databases store, organize, and manage data efficiently, allowing applications to retrieve and manipulate information seamlessly.

---
💡 **Virtualization**

-> Installing Multiple Guest Operating Systems in one Host Operating System, allowing developers to create isolated environments for various projects without hardware limitations.

-> 🖥️ Hypervisor S/w will be used to achieve this, acting as a virtual machine monitor (VMM) that manages and allocates resources between host and guest operating systems.

-> 👻 We need to install all the required software in HOST OS to run our application, which can become cumbersome when managing dependencies across different projects.

-> ⏳ It is an old technique to run the applications, having been widely used before containerization technologies emerged to provide more lightweight solutions.

-> 🔥 System performance will become slow in this process due to resource-heavy virtual machines, leading to inefficient hardware usage and longer load times.

-> ✅ To overcome the problems of Virtualization, we are going for Containerization concept, a modern approach that solves these issues with lightweight, portable, and fast containers.

---
🛠️ **Docker**

-> Docker is a containerization platform that enables developers to create, deploy, and manage containers easily and efficiently.

-> 🌟 Docker is used to simplify application deployment process in Multiple Environments (DEV, SIT, UAT, PILOT, and PROD), ensuring consistency across all stages of software development.

-> 🔧 Docker is used to package application code + application dependencies for easy execution, creating a reproducible environment for any machine.

-> 🏢 Using Docker, we will create Docker images, which act as blueprints for containers and contain everything necessary to run the application.

-> 📚 Docker Image contains App code + App dependencies, such as libraries, frameworks, and environment configurations, ensuring smooth operation regardless of the host machine.

-> 🔧 We can run docker image on any machine. It will take care of dependencies & execution, making development and deployment seamless and predictable.

-> 💡 When we run Docker image, it will create Docker container, which is a live instance of the application environment.

-> 🏦 Docker Container will run our application in an isolated, secure, and efficient manner, improving portability and minimizing configuration issues.

---
💥 **Docker Images**

-> 💥 Docker images are lightweight, standalone, executable packages that contain everything needed to run a piece of software, including the code, runtime, libraries, and dependencies, ensuring smooth and reliable deployments.

-> 🔧 They are built from Dockerfile instructions, which specify the environment and steps to create the image, providing a clear, repeatable blueprint for container creation.

-> 💡 Images are stored in repositories, like Docker Hub, and can be easily shared and distributed across different environments, facilitating collaboration and efficient deployment workflows.

-> 🌿 Docker images promote consistency and reproducibility in software deployment by encapsulating the application and its dependencies, eliminating "works on my machine" issues.

-> 👨‍💻 They enable developers to isolate applications from the underlying infrastructure, leading to more portable and scalable deployments, which is essential in modern microservices architectures.

-> 🌟 Docker images support versioning, allowing teams to manage different versions of applications and roll back changes if necessary, ensuring smooth updates and reliable releases.

---
🏦 **Containerization**

-> 👉 It is used to package all the software and application code in one container for execution, creating a portable and isolated environment.

-> 🌟 Container will take care of everything which is required to run our application, including dependencies, runtime, and configuration.

-> 🌎 We can run the containers on Multiple Machines easily, ensuring consistency and reducing the time needed to set up environments.

-> 🛠️ Docker is a containerization software that simplifies the packaging and distribution of applications, reducing deployment errors.

-> 🏢 Using Docker, we will create a container for our application, ensuring it runs consistently across development, testing, and production environments.

-> 💡 Using Docker, we will create an image for our application, capturing the complete software environment in a reusable format.

-> 🔗 Docker images we can share easily to multiple machines, enabling rapid deployment and scaling of applications.

-> 💥 Using Docker image we can create a docker container and we can execute it, making deployment fast, reliable, and repeatable, while simplifying infrastructure management and enhancing productivity for development teams.



---
🐳 **Install Docker in Linux VM**

👉 **Log in to AWS account**

- Open your web browser and go to the AWS Management Console.
- Enter your login credentials and access your AWS account dashboard.
- If you don’t already have an account, create one by following the signup process.

👉 **Create a Linux Virtual Machine using Amazon Linux AMI**

- Navigate to the EC2 service from the AWS console.
- Launch a new instance and select "Amazon Linux AMI" as the machine image.
- Configure the instance with desired specs, such as CPU, memory, and storage.
- Make sure to open port 22 (SSH) in the security group to allow remote connections.
- Launch the instance and note down the public IP address or DNS name.

👉 **Connect to the Linux VM using MobaXterm**

- Open MobaXterm on your local machine.
- Create a new SSH session and enter the EC2 instance's public IP address.
- Use the key pair (PEM file) associated with the instance to authenticate.
- Connect to your Linux VM and ensure you have terminal access.

👉 **Execute the below commands to install Docker s/w**

```bash
$ sudo yum update -y   🔄   # Update the package manager
$ sudo yum install docker -y   📥   # Install Docker
$ sudo service docker start   ▶️   # Start the Docker service
```

✅ **Add ec2-user to docker group by executing below command (to give docker permissions to ec2-user account)**

```bash
$ sudo usermod -aG docker ec2-user   🔐
```

🚪 **Close the terminal**

```bash
$ exit   ❌
```

👉 **Then press 'R' to restart the session (This is in MobaXterm)**

✅ **Execution below command to see docker status**

```bash
$ docker --version   🐋   # Check Docker version
$ docker info   ℹ️   # Get detailed information about Docker installation
```

---
🛠️ **Basic Docker Commands**

✅ **Display docker images available on our machine**

```bash
$ docker images   🖼️
```

- Lists all Docker images stored locally on the machine.
- Shows image ID, repository, tag, size, and creation date.

✅ **Download docker image**

```bash
$ docker pull <image-name / image-id>   📥
```

- Pulls the specified Docker image from Docker Hub or another container registry.
- Ensures the image is available locally for running containers.

✅ **Run docker image**

```bash
$ docker run <image-name / image-id>   ▶️
```

- Creates and starts a new Docker container from the specified image.
- Use optional flags like -d (detached mode) or -p (port mapping).

✅ **Delete docker image**

```bash
$ docker rmi <image-name / image-id>   🗑️
```

- Removes the specified Docker image from the local machine.
- Use -f flag to force deletion if the image is in use.

✅ **Display all running docker containers**

```bash
$ docker ps   📋
```

- Lists active Docker containers.
- Shows container ID, name, image, status, ports, and command.

✅ **Display all running and stopped containers**

```bash
$ docker ps -a   📋
```

- Lists both running and stopped containers.
- Useful for viewing container history and troubleshooting.

✅ **Delete docker container**

```bash
$ docker rm <container-name / container-id>   🗑️
```

- Removes the specified Docker container.
- Container must be stopped before deletion.

✅ **Delete docker image forcefully**

```bash
$ docker rmi -f <image-name / image-id>   ⚠️
```

- Forces the deletion of a Docker image.
- Useful when the image is being referenced by stopped containers.

✅ **Stop Docker container**

```bash
$ docker stop <container-name / container-id>   ⏹️
```

- Gracefully stops a running Docker container.
- Allows processes inside the container to shut down properly.

✅ **Delete all stopped containers and unused images and unused networks**

```bash
$ docker system prune -a   🧹
```

- Cleans up unused Docker data, including containers, images, and networks.
- Helps free up disk space and keep Docker environment tidy.

---
🐳 **Dockerfile**

👉 **Dockerfile contains instructions to build a docker image**

- A Dockerfile is a text file containing all the commands needed to assemble a Docker image.
- It allows automation of image creation and ensures consistency across environments.

👉 **In Dockerfile, we will use DSL (Domain Specific Language) keywords**

- These keywords tell Docker how to construct the image step-by-step.
- Instructions are executed sequentially, from top to bottom.

👉 **Docker engine will process Dockerfile instructions from top to bottom**

✅ **Below are the Dockerfile Keywords**

- **FROM**   📦  - Sets the base image for the Dockerfile.
- **MAINTAINER**   👤  - Specifies the author or maintainer of the image.
- **COPY**   📋  - Copies files from the host to the Docker image.
- **ADD**   ➕  - Adds files from the host, supports archives and remote URLs.
- **RUN**   ▶️  - Executes commands to install packages and dependencies.
- **CMD**   🚀  - Provides default commands when a container runs.
- **ENTRYPOINT**   🔐  - Defines a fixed command that runs every time the container starts.
- **ENV**   🌍  - Sets environment variables within the container.
- **LABEL**   🏷️  - Adds metadata to the image.
- **WORKDIR**   🏠  - Sets the working directory inside the container.
- **EXPOSE**   🔓  - Informs Docker that the container listens on specified ports.
- **VOLUME**   🗂️  - Creates a mount point for external volumes.

This guide should help you get Docker up and running smoothly on your Linux VM! 🚀

---
🛡️ FROM
-> **FROM** keyword is used to represent the base image to create our image. It is the foundation of every Docker image, and without it, a Dockerfile cannot exist.
-> On top of the base image, our image will be created, which allows us to customize the environment as needed.

🧑‍🍳 **Syntax:**

```
FROM java:jdk-1.8
FROM tomcat:9.5
FROM mysql:6.8
FROM python:3.3
```

👉 We can use multiple **FROM** instructions in a single Dockerfile, creating multi-stage builds. This is particularly useful for optimizing Docker images, allowing us to copy only the necessary artifacts into the final production image while keeping intermediate stages clean and lightweight.

---
👨‍💻 MAINTAINER
-> **MAINTAINER** keyword is used to specify Dockerfile author information, helping others to know who created the image.
-> Although this instruction is still valid, it is now considered deprecated. It is recommended to use **LABEL** instead to add metadata to your image.

📋 **Syntax:**

```
MAINTAINER Vanna [vanna@inofotech.com](mailto:vanna@inofotech.com)
```

✅ **Modern Syntax:**

```
LABEL maintainer="Vanna <vanna@inofotech.com>"
```

---
📁 COPY
-> **COPY** command is used to copy files from source to destination while creating a docker image. It is commonly used to move application code or configuration files.
-> COPY only works with local files; it cannot access remote URLs or extract archives.

🧑‍🍳 **Syntax:**

```
COPY  
```

✅ **Ex:**

```
COPY target/sbi-app.war /app/tomcat/webapps/sbi-app.war
```

👉 Best practice: Always include a **.dockerignore** file to avoid copying unnecessary files into the Docker image, which could increase its size.

---
📦 ADD
-> **ADD** command is also used to copy files from source to destination while creating a docker image. It has additional features that COPY does not provide.
-> Unlike COPY, ADD can extract tar archives automatically and can pull files from remote URLs.

🧑‍🍳 **Syntax:**

```
ADD  
```

✅ **Ex:**

```
ADD  /app/tomcat/webapps/sbi-app.war
```

❓ **Q) What is the difference between COPY and ADD commands?**

👉 **COPY:** Just copies the files from one path to another path within the machine. It is simpler and more predictable.
👉 **ADD:** Copies files from one path to another path and supports source location as a URL also. It can also unpack compressed files, which can be convenient but may introduce unexpected behavior.

⚠️ **Best Practice:** Use COPY unless you specifically need the extra functionality that ADD provides. This makes your Dockerfile more predictable and secure.

---
⚙️ RUN
-> **RUN** instructions will execute while creating the image. These commands help install dependencies, update packages, and configure the environment.
-> Using RUN, we can give instructions to Docker to execute commands inside the image, such as installing software packages or setting up configurations.
-> We can write multiple RUN instructions; Docker will process all the RUN instructions from top to bottom, creating new image layers for each instruction.

🚀 **Example:**

```
RUN yum install maven
RUN yum install git
RUN git clone repo-url
RUN mvn clean package
```

👉 For better image performance, combine multiple RUN instructions into a single RUN statement using backslashes and logical operators. This reduces the number of intermediate layers in the image.

✅ **Optimized Example:**

```
RUN yum install -y maven git \ 
    && git clone repo-url \ 
    && mvn clean package
```

---
🚀 CMD
-> **CMD** instructions will execute while creating the container, not the image.
-> Using CMD command, we can run our application package file jar/war file or start a server.
-> CMD provides defaults for an executing container; it’s like saying, "When this container starts, do this by default."

✅ **Example:**

```
CMD sudo start tomcat
```

⚠️ **Note:** If we write multiple CMD instructions, Docker will process only the last CMD instruction. There is no use in writing multiple CMD instructions in one Dockerfile.

❓ **Q) What is the difference between RUN and CMD in Dockerfile?**

👉 **RUN:** Used to execute instructions while creating an image. Produces new layers in the Docker image.
👉 **CMD:** Used to execute instructions while creating a container. It does not create a new image layer; it just specifies what should happen when the container runs.

✨ **Key Differences:**
- Multiple RUN instructions are processed one by one, creating new image layers with each command.
- Only the last CMD instruction is processed in a Dockerfile, and it serves as the default command when the container starts.
- If you need to override the CMD at runtime, you can pass arguments to the docker run command.

✅ **Pro Tip:** Use CMD to define the default container behavior, but use **ENTRYPOINT** if you want to enforce the execution of a specific command and still allow users to supply additional arguments.

👉 By understanding these Dockerfile instructions deeply, you can create optimized, secure, and efficient Docker images!

Here's your document with emojis added while keeping all the content intact:

---
### 🚢 Sample Dockerfile 🐳
FROM ubuntu 🐧

MAINTAINER Vanna 📧 [vanna@inofotech.com](mailto:vanna@inofotech.com)

RUN echo "Hi, I am RUN-1" 🏃‍♂️

RUN echo "Hi, I am RUN-2" 🏃‍♀️

CMD echo "Hi, I am CMD-1" 🎙️

RUN echo "Hi, I am RUN-3" 🏃

CMD echo "Hi, I am CMD-2" 🎤

➡️ Save the above content in the Dockerfile 📄

**Filename:** `Dockerfile`

---

### 🚀 Command to create a Docker image using Dockerfile
📝 **Syntax:** `$ docker build -t <image-name> .`

📌 **Example:** `$ docker build -t myfirstimage .`

---

### ▶️ Command to run a Docker image
```bash
$ docker run myfirstimage
```  

---

### 🔐 Command to login with the Docker Hub account
```bash
$ docker login
```  
⚠️ **Note:** We need to enter our Docker Hub account credentials correctly (it will ask only the first time).

---

### 🏷️ Command to tag our Docker image
```bash
$ docker tag <source-image> <target-image>
```  
📌 **Example:** `$ docker tag myfirstimage vanna/myfirstimage`

---

### 📤 Command to push the Docker image to Docker Hub
```bash
$ docker push <image-name>
```  
📌 **Example:** `$ docker push vanna/myfirstimage`

---

### 🧹 Delete all unused images and stopped containers
```bash
$ docker system prune -a
```  

---

### 📥 Pull the image from Docker Hub
```bash
$ docker pull vanna/myfirstimage
```  

### ▶️ Run the image
```bash
$ docker run vanna/myfirstimage
```  

---

### 📌 **Note:**
We can use a customized name for the Dockerfile. If we change the Dockerfile name, we need to pass the filename as input for the Docker build command using the `-f` option, like below:
```bash
$ docker build -f <custom-filename> -t <image-name> .
```  

---
## 🔗 ENTRYPOINT

➡️ **ENTRYPOINT** instructions will execute while creating a container.

📌 **Syntax:**
```dockerfile
ENTRYPOINT [ "echo" , "Welcome to Vanna IT" ]
```
```dockerfile
ENTRYPOINT [ "java", "-jar", "target/boot-app.jar" ]
```  

❓ **Q) What is the difference between CMD and ENTRYPOINT?**

✅ **CMD:** We can override `CMD` instructions at runtime while creating a container.

🚫 **ENTRYPOINT:** We **can't** override `ENTRYPOINT` instructions.

---

## 📂 WORKDIR
➡️ **WORKDIR** is used to set the working directory for an image/container.

📌 **Example:**
```dockerfile
WORKDIR /app/
```  

⚠️ **Note:** The Dockerfile instructions available **after** `WORKDIR` will be processed **from the given working directory**.

---

## 🌎 ENV
➡️ **ENV** is used to set environment variables.

📌 **Example:**
```dockerfile
ENV java /etc/softwares/java
```  

---

## 🔄 ARG
➡️ **ARG** is used to remove hardcoded values.  
➡️ Using `ARG`, we can pass values at runtime like below:

📌 **Example:**
```dockerfile
ARG branch
RUN git clone -b $branch <repo-url>
```  
```bash
$ docker build -t imageone --build-arg branch=master .
```  

---

## 🔥 EXPOSE
➡️ **EXPOSE** is used to specify our container running **PORT**.

📌 **Example:**
```dockerfile
EXPOSE 8080
```  

⚠️ **Note:** This is just a **documentation command** to provide the container's running port number.

---

## 💾 VOLUME
➡️ **VOLUME** is used to specify **Docker container data storage location**.

⚠️ **Note:** Volumes are used for **storage**.

---

📌 **Dockerfile Keywords:**  
`FROM` 🏗️  
`MAINTAINER` 👤  
`COPY` 📂  
`ADD` ➕  
`RUN` ⚡  
`CMD` 🎙️  
`ENTRYPOINT` 🔗  
`WORKDIR` 📂  
`USER` 👨‍💻  
`ENV` 🌎  
`ARG` 🔄  
`EXPOSE` 🔥  
`VOLUME` 💾

---
 🚀
**Dockerize Spring Boot Application**

🔹 **Spring Boot** is one ready-made Java-based framework available in the market to develop Java-based applications quickly and efficiently. It removes a lot of configuration overhead and provides a convention-over-configuration approach, making development faster and more productive.

🔹 **Spring Boot** provides an embedded server (an internal server will be available, so we don’t need to configure a server for execution manually). This simplifies deployment and allows the application to be run independently without needing an external application server.

🔹 **Spring Boot application** will be packaged as a JAR file (**mvn clean package** goal will do that packaging). This makes it easier to manage, distribute, and deploy across different environments.

⚠️ **Note:** When we do a Maven package, the project JAR will be created in the project's `target` folder, which contains all compiled classes, dependencies, and required resources.

🔹 To run Spring Boot applications, we just need to run the JAR file like below:

```bash
$ java -jar myapp.jar
```
---
## 🐳 **Dockerfile**

A Dockerfile is a script containing a series of instructions on how to build a Docker image. Below is the Dockerfile to containerize a Spring Boot application:

```dockerfile
FROM openjdk:11

COPY target/spring3fakerapiswagger.jar /usr/app/

WORKDIR /usr/app/

ENTRYPOINT ["java", "-jar", "spring3fakerapiswagger.jar"]
```

---

📌 **Spring Boot App Git Repo URL:** [🔗 GitHub Repo](https://github.com/kumarsatish23/spring3fakerapiswagger.git)

📥 **Clone Git Repo:**
```bash
$ git clone https://github.com/kumarsatish23/spring3fakerapiswagger.git
```

📂 **Navigating to the project folder:**
```bash
$ cd spring3fakerapiswagger
```

⚙️ **Execute Maven goals:**
```bash
$ mvn clean package
```

⚠️ **Note:** After the package is successfully created, we can see the project JAR file in the `target` folder.

🐳 **Create a Docker image:**
```bash
$ docker build -t sb-app .
```

🚀 **Run a Docker image with port mapping:**
```bash
$ docker run -p 8080:8080 sb-app
```

---
## ⚓ How to run Docker container in Detached Mode**

❌ With the below command, our terminal will be blocked, and we can't execute any other command. To execute other commands, we need to type `CTRL+C`, then the terminal will open for command execution, but our container will stop.

```bash
$ docker run -p 8080:8080 kumarsatish23/sb-app
```

💡 **Solution:** To overcome this, we can pass `-d` to run the container in **detached mode**. This will keep the container running while allowing us to execute other commands in the terminal.

```bash
$ docker run -d -p 8080:8080 kumarsatish23/sb-app
```

📌 **Check running containers:**
```bash
$ docker ps
```

📜 **Check logs of the container:**
```bash
$ docker logs
```

---
## 📦Dockerizing Java Web Application (Without Spring Boot)**

🔹 Java web applications are packaged as **WAR** (Web Archive) files, which contain servlets, JSP files, and other necessary resources.

🔹 A **WAR file** contains application code, including all necessary libraries and configurations, making it portable across different environments.

🔹 To run the WAR file, we need a **web server** (e.g., **Apache Tomcat**). The web server serves as a runtime environment for handling requests and responses for web applications.

🔹 The WAR file must be **deployed** in a **Tomcat Server** for execution, where it gets extracted and run.

🔹 In the Tomcat server, we will have a **webapps** folder for deployment, where the WAR file should be placed.

⚠️ **Note:** To run Java web applications, we need `Java` & `Tomcat` as dependencies.

---
🐳 **Dockerfile**

A Dockerfile for a Java web application deployed in Tomcat:

```dockerfile
FROM tomcat:8.0.20-jre8

COPY target/01-maven-web-app.war /usr/local/tomcat/webapps/maven-web-app.war
```

---

📌 **Java Web App Git Repo URL:** [﻿🔗 GitHub Repo](https://github.com/kumarsatish23/spring3fakerapiswagger.git)

📥 **Clone Git Repo:**
```bash
$ git clone https://github.com/kumarsatish23/spring3fakerapiswagger.git
```

📂 **Navigate to the project folder:**
```bash
$ cd maven-web-app
```

⚙️ **Execute Maven goals:**
```bash
$ mvn clean package
```

🐳 **Create a Docker image:**
```bash
$ docker build -t maven-web-app .
```

📸 **List available Docker images:**
```bash
$ docker images
```

🚀 **Run the Docker container:**
```bash
$ docker run -d -p 8080:8080 maven-web-app
```

📌 **Check running containers:**
```bash
$ docker ps
```

📜 **Check logs of the container:**
```bash
$ docker logs
```

⚠️ **Note:** In the above URL, `maven-web-app` is called a **context path** (the name of the WAR file becomes the context path). It is important to remember that the context path determines how the application is accessed in a browser (e.g., `http://localhost:8080/maven-web-app`).

