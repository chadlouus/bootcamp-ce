# Lab 2 - Deploy A Front-End React Application on IBM Code Engine
## Clone the project Locally
```
git clone https://github.com/chadlouus/carbon-react-admin.git
```
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

## Deploy the Docker Image on IBM Code Engine

### Create a new Application inside the CE project
1. From your own CE project, click on `Applications` link
1. Click `Create` button
1. Enter the name of `carbon-react-admin`
1. Accept the default Container image selection
1. Under `Image reference`, enter `websphere-liberty`
1. For `Listening port`, enter `7001`
7. For `CPU and memory`, select `0.125 vCPU / 0.25 GB`
8. Accept the default values for other fields, and click on `Create` button

### Verify the Application
1. Click on `Test application` button
2. Click on `Application URL`
3. Verify that the Carbon-react-admin application is deployed on IBM Code Engine

