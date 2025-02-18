# VannaInfoTech

# ===================
Docker
Application Tech Stack: It represents technologies used in the application

1. Frontend Stack: HTML, CSS, JS, BS & Angular / React JS
2. Backend Stack: Java / .Net / Python / Node JS
3. Database: Oracle / MySQL / PostgresSQL / Mongo DB
# ===============
Virtualization
-> Installing Multiple Guest Operating Systems in one Host Operating System

-> Hypervisor S/w will be used to achieve this

-> We need to install all the required software in HOST OS to run our application

-> It is an old technique to run the applications

-> System performance will become slow in this process

-> To overcome the problems of Virtualization, we are going for Containerization concept

# ========
Docker
-> Docker is a containerization platform

-> Docker is used to simplify application deployment process in Multiple Environments
(DEV, SIT, UAT, PILOT, and PROD)

-> Docker is used to package application code + application dependencies for easy execution

-> Using Docker, we will create Docker images

-> Docker Image contains App code + App dependencies

-> We can run docker image on any machine. It will take care of dependencies & execution

-> When we run Docker image, it will create Docker container

-> Docker Container will run our application

# =================
Docker Images
->Docker images are lightweight, standalone, executable packages that contain everything needed to run a piece of software, including the code, runtime, libraries, and dependencies.

->They are built from Dockerfile instructions, which specify the environment and steps to create the image.

->Images are stored in repositories, like Docker Hub, and can be easily shared and distributed across different environments.

->Docker images promote consistency and reproducibility in software deployment by encapsulating the application and its dependencies.

->They enable developers to isolate applications from the underlying infrastructure, leading to more portable and scalable deployments.

->Docker images support versioning, allowing teams to manage different versions of applications and roll back changes if necessary.

# =================
Containerization
-> It is used to package all the software and application code in one container for execution

-> Container will take care of everything which is required to run our application

-> We can run the containers on Multiple Machines easily

-> Docker is a containerization software

-> Using Docker, we will create a container for our application

-> Using Docker, we will create an image for our application

-> Docker images we can share easily to multiple machines

-> Using Docker image we can create a docker container and we can execute it

# =======================
Install Docker in Linux VM
-> Log in to AWS account

-> Create a Linux Virtual Machine using Amazon Linux AMI

-> Connect to the Linux VM using MobaXterm

-> Execute the below commands to install Docker s/w

$ sudo yum update -y
$ sudo yum install docker -y
$ sudo service docker start

# add ec2-user to docker group by executing below command (to give docker permissions to ec2-user account)
$ sudo usermod -aG docker ec2-user

# Close the terminal
$ exit

Then press 'R' to restart the session (This is in MobaXterm)

# execution below command to see docker status
$ docker --version

$ docker info

# =====================
Basic Docker Commands
# display docker images available on our machine
$ docker images

# download docker image
$ docker pull <image-name / image-id>

# Run docker image
$ docker run <image-name / image-id>

# Delete docker image
$ docker rmi <image-name / image-id>

# Display all running docker containers
$ docker ps

# display all running and stopped containers
$ docker ps -a

# Delete docker container
$ docker rm 

# Delete docker image forcefully
$ docker rmi -f 

# Stop Docker container
$ docker stop 

# Delete all stopped containers and unused images and unused networks
$ docker system prune -a

# ==========
Dockerfile
-> Dockerfile contains instructions to build a docker image

-> In Dockerfile, we will use DSL (Domain Specific Language) keywords

-> Docker engine will process Dockerfile instructions from top to bottom

-> Below are the Dockerfile Keywords

FROM
MAINTAINER
COPY
ADD
RUN
CMD
ENTRYPOINT
ENV
LABEL
WORKDIR
EXPOSE
VOLUME

# =============
FROM
-> FROM keyword is used to represent the base image to create our image
-> On Top of the base image, our image will be created

Syntax:

FROM java:jdk-1.8
FROM tomcat:9.5
FROM mysql:6.8
FROM python:3.3

# =============
MAINTAINER
-> MAINTAINER keyword is used to specify Dockerfile author information

Syntax:

MAINTAINER Vanna [﻿vanna@inofotech.com](mailto:vanna@inofotech.com) 

# =======
COPY
-> COPY command is used to copy files from source to destination while creating a docker image

Syntax:

COPY  

Ex:

COPY target/sbi-app.war /app/tomcat/webapps/sbi-app.war

# =======
ADD
-> ADD command is also used to copy files from source to destination while creating a docker image

Syntax:

ADD  

ADD  

Ex:

ADD  /app/tomcat/webapps/sbi-app.war

Q) What is the difference between COPY and ADD commands?

-> Using COPY command we can just copy the files from one path to another path within the machine

-> Using ADD command we can copy files from one path to another path and it supports source location as a URL also.

# =======
RUN
-> RUN instructions will execute while creating the image

-> Using RUN, we can give instructions to docker to execute commands

-> We can write multiple RUN instructions, docker will process all the RUN instructions from top to bottom

## Example
RUN yum install maven
RUN yum install git
RUN git clone repo-url
RUN mvn clean package

# =======
CMD
-> CMD instructions will execute while creating the container

-> Using CMD command we can run our application package file jar / war file

## Example
CMD sudo start tomcat

Note: If we write multiple CMD instructions also docker will process only the last CMD instruction. There is no use of writing multiple CMD instructions in one Dockerfile.

Q) What is the difference between RUN and CMD in Dockerfile?

-> RUN is used to execute instructions while creating an image
-> CMD is used to execute instructions while creating a Container

-> We can write multiple RUN instructions in Dockerfile, docker will process all those instructions one by one.
-> If we write multiple CMD instructions in Dockerfile, docker will process only the last CMD instruction.

# ==================
Sample Dockerfile
FROM ubuntu

MAINTAINER Vanna [﻿vanna@inofotech.com](mailto:vanna@inofotech.com) 

RUN echo "Hi, I am RUN-1"

RUN echo "Hi, I am RUN-2"

CMD echo "Hi, I am CMD-1"

RUN echo "Hi, I am RUN-3"

CMD echo "Hi, I am CMD-2"

-> Save the above content in the Docker file

filename: Dockerfile

# Command to create a docker image using dockerfile
Syntax: $ docker build -t  .

Ex: $ docker build -t myfirstimage .

# Command to run a docker image
$ docker run myfirstimage

# Command to login with the dockerhub account
$ docker login

Note: We need to enter our dockerhub account credentials correctly (it will ask only the first time)

# Command to tag our docker image
$ docker tag  

Ex: $ docker tag myfirstimage vanna/myfirstimage

# command to push the docker image to the docker hub account
$ docker push <imagesname-ex:vanna/myfirstimage.

Note: Delete all unused images and stopped containers

$ docker system prune -a

# Pull the image from the docker hub
$ docker pull vanna/myfirstimage

# Run the image
$ docker run vanna/myfirstimage

Note: We can use a customized name also for the dockerfile. When we change the dockerfile name we need to pass the filename as input for docker build command using the -f option like below.

$ docker build -f  -t  .

# ============
ENTRYPOINT
-> ENTRYPOINT instructions will execute while creating a container

Syntax --------- ENTRYPOINT [ "echo" , "Welcome to Vanna IT" ]

ENTRYPOINT [ "java", "-jar", "target/boot-app.jar" ]

Q) What is the difference between CMD and ENTRYPOINT?

-> We can override CMD instructions at runtime while creating a container

-> We can't override ENTRYPOINT instructions

# ==========
WORKDIR
-> It is used to set the working directory for an image / container

Ex:

WORKDIR /app/

Note: The Dockerfile instructions which are available after WORKDIR those instructions will be processed from the given working directory.

# ======
ENV
-> ENV is used to set Environment Variables

Ex:

ENV  

ENV java /etc/softwares/java

# ====
ARG
-> It is used to remove hardcoded values

-> Using ARG we can pass values in runtime like below

Ex:

ARG branch

RUN git clone -b $branch 

$ docker build -t imageone --build-arg branch=master

# ========
EXPOSE
-> It is used to specify our container running PORT

Ex:

EXPOSE 8080

Note: It is just like a documentation command to provide container running port number.

# ========
VOLUME
-> VOLUME is used to specify docker container data storage location.

Note: Volumes are used for storage.

FROM MAINTAINER COPY ADD RUN CMD ENTRYPOINT WORKDIR USER ENV ARG EXPOSE VOLUME

# ==============================
Dockerize Spring Boot Application
-> Spring Boot is one ready-made java-based framework available in the market to develop java-based applications quickly

-> Spring Boot is providing an embedded server (internal server will be available, we no need to configure a server for execution)

-> Spring Boot application will be packaged as a jar file (mvn clean package goal will do that package)

Note: When we do maven package, project jar will be created in the project target folder

-> To run spring boot applications we just need to run the jar file like below

$ java -jar 

---------------------------------Dockerfile------------------------------------

FROM openjdk:11

COPY target/spring3fakerapiswagger.jar /usr/app/

WORKDIR /usr/app/

ENTRYPOINT ["java", "-jar", "spring3fakerapiswagger.jar"]

---

Spring Boot App Git Repo URL: [﻿https://github.com/kumarsatish23/spring3fakerapiswagger.git](https://github.com/kumarsatish23/spring3fakerapiswagger.git) 

# Clone Git Repo
$ git clone [﻿https://github.com/kumarsatish23/spring3fakerapiswagger.git](https://github.com/kumarsatish23/spring3fakerapiswagger.git) 

# Navigating to the project folder
$ cd spring3fakerapiswagger

# execute maven goals
$ mvn clean package

Note: After the package got success, we can see the project jar file in the target folder.

# create a docker image
$ docker build -t sb-app .

# run a docker image with port mapping
$ docker run -p 8080:8080 sb-app

# ======================================
How to run Docker container in Detached Mode
=> With the below command our terminal will be blocked, we can't execute any other command. To execute other commands we need to type CTRL+C then the terminal will open for commands execution but our container gets stopped.

$ docker run -p 8080:8080 kumarsatish23/sb-app

Note: To overcome the above problem we can pass '-d' to run the container in detached mode. When we execute the below command it will run the container in detached mode and it will open the terminal for commands execution.

$ docker run -d -p 8080:8080 kumarsatish23/sb-app

=> Once the above command is executed, we can see running containers using the below command

$ docker ps

=> We can check logs of the container using the below command

$ docker logs 

# ================================================
Dockerizing Java Web Application (Without SpringBoot)
-> Java web applications will be packaged as a war file

-> WAR (Web Archive) contains application code

-> To run the war file we need a web server (Ex: Apache Tomcat)

-> We need to deploy the war file in Tomcat Server for Execution

-> In Tomcat server we will have "webapps" folder for deployment

Note: To run normal java web applications we need "java & tomcat" as dependencies

---------------------------------------------------Dockerfile----------------------------------------------------

FROM tomcat:8.0.20-jre8

COPY target/01-maven-web-app.war /usr/local/tomcat/webapps/maven-web-app.war

---

############### Java Web App Git Repo : [﻿https://github.com/kumarsatish23/spring3fakerapiswagger.git](https://github.com/kumarsatish23/spring3fakerapiswagger.git) ############

$ git clone [﻿https://github.com/kumarsatish23/spring3fakerapiswagger.git](https://github.com/kumarsatish23/spring3fakerapiswagger.git) 

$ cd maven-web-app

$ mvn clean package

$ docker build -t maven-web-app .

$ docker images

$ docker run -d -p 8080:8080 maven-web-app

$ docker ps

$ docker logs 

Note: In the above URL "maven-web-app" is called as a context path (name of the war file will become context path)

