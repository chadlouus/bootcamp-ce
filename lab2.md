# Lab 2 - Deploy A Front-End React Application on IBM Code Engine
## Clone the project Locally
```
git clone https://github.com/chadlouus/carbon-react-admin.git
```
Review the following pages in the application to get a feeling for how the application is composed of.

1. the App page - client/src/components/Admin/index.jsx
2. the main page for the right-hand side - client/src/components/resources/MainPage/index.js
3. for dataProvider - https://jsonplaceholder.typicode.com/
4. the menu page for Posts and Photos - client/src/components/Admin/menuList.js

## Run a local build
Building a Local Docker Image
```sh
docker build -t carbon-react-admin .
```
## Testing the Local Docker Image
docker run --rm -p 7001:7001 carbon-react-admin

## Verify Local Docker Container
Verify the following URLs on a browser, where `IP_ADDRESS` is the ip address of your VM, or use `localhost` if you are not using a VM
1. http://IP_ADDRESS:7001/

After verifying, press Ctrl-C to stop the container.

## Create a Container Registry Namespace
1. Click on the Hamburger menu in IBM Cloud Console
1. Scroll down the side bar menu, and select `Container Registry`, then `Namespaces`
1. Make sure the `Location` shows the closest region to you, such as "Dallas" or "Sao Paulo"
1. Click on the `Create` button
2. Enter a name of `cr-bootcamp-devN` where N is your assigned developer number, such as dev3
3. Click on `Create` button to create the namespace

## Deploy the Docker Image on IBM Code Engine

### Create a new Application inside the CE project
1. From your own CE project, click on `Applications` link
1. Click `Create` button
1. Enter the name of `carbon-react-admin`
1. Accept the default Container image selection
1. Under `Image reference`, enter `private.us.icr.io/ce-bootcamp-us-devN`, where `N` is your assigned developer number, such as 3
1. For `Listening port`, enter `7001`
7. For `CPU and memory`, select `0.125 vCPU / 0.25 GB`
8. Accept the default values for other fields, and click on `Create` button

### Verify the Application
1. Click on `Test application` button
2. Click on `Application URL`
3. Verify that the Carbon-react-admin application is deployed on IBM Code Engine

