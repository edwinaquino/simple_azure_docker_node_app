# Simple Azure Docker Demo App

> Use this app to deploy a Docker container from your local machine into the Azure Container services. This is a very simple Nodejs hello world example app. You can use this app to build and push it to a docker container as well as to an Azure container registry.

## App Info

This is a "Hello World" Node/Express web application you can use for building and running in a Docker container as well as other container cloud services like Azure.

## Requirements
* Docker
* NodeJs
* Azure Account

## Getting Started
To get started follow these steps below. In this example, we are going to create a app called "simple_azure_docker_node_app"

1. Clone this repository<br>
```$ git clone https://github.com/edwinaquino/simple_azure_docker_node_app.git```
2. Change directory into the app.<br>
```$ cd simple_azure_docker_node_app```<br>
3. Send command: Build the nodejs application, this will create the node_modules folder.<br>
```$ npm install```
4. Build the docker container in your local machine.<br>
```$ docker build -t simple_azure_docker_node.azurecr.io/node-web-app .```
5. Run the app in your local machine container.<br>
```$ docker run -p 49160:8080 -d simple_azure_docker_node.azurecr.io/node-web-app```

6. open: http://localhost:49160/

7. Create Container Registry in Azure. From this registry, obtain the user name and password go to the Settings > Access Keys
![7-container-registry](https://user-images.githubusercontent.com/30946443/106708305-7d3c9c00-65a7-11eb-9410-9354d8c5bebd.jpg)


8. $ docker login simple_azure_docker_node.azurecr.io
![7-1-container-registry](https://user-images.githubusercontent.com/30946443/106708248-6302be00-65a7-11eb-8b6b-767f4e3e3ba0.jpg)


9. Push the docker image to azure docker registry. This will make a copy of the local environment into the azure cloud.<br>
```$ docker push simple_azure_docker_node.azurecr.io/node-web-app```<br>
When completed, go to the Azure portal under the container registry and into repositories. This is where we are going to put our instance.

__Create an Azure Container Instance using these settings:__<br>
Home > Create Resource > Containers web app
**Basic Tab:*
* Appname: simple_azure_docker_node-ci
* publish: Docker Container 
* OS Linux:
* Region: CENTRAL

__Docker Tab:__
* options: single 
* Image Source: Azure Container Registry: 
* Registry: simple_azure_docker_node 
* image: node-web-app
* tag: latest

Hit the create button

This will take about 10 minutes to create. After about 10 minutes, you can confirm your app by opening the URL in your browser:
https://simple_azure_docker_node.azurewebsites.net/

Hope that works for you.

### Author

Edwin Aquino

### Version

1.0

### License

This project is licensed under the Apache License 2.0
