# Lab 1 - Deploy Websphere Liberty on IBM Code Engine
## Run websphere-liberty Docker Image Locally
```
docker run --rm -p 9080:9080 websphere-liberty
```
Verify the following URLs on a browser, where `IP_ADDRESS` is the ip address of your VM, or use `localhost` if you are not using a VM
1. http://IP_ADDRESS:9080
2. http://IP_ADDRESS:9080/health
3. http://IP_ADDRESS:9080/openapi

After verifying, press Ctrl-C to stop the container.

## Deploy the Docker Image on IBM Code Engine
### Create a new Code Engine project
Go to https://cloud.ibm.com/codeengine/projects

Create a new Code Engine Project by the name of `CE-bootcamp-devN` where N is your assigned number, such as 3

### Create a new Application inside the CE project
1. From the newly created CE project, click on `Applications` link
2. Click `Create` button
3. Enter the name of `websphere-liberty`
4. Accept the default Container image selection
5. Under `Image reference`, enter `websphere-liberty`
6. For `Listening port`, enter `9080`
7. For `CPU and memory`, select `0.125 vCPU / 0.25 GB`
8. Accept the default values for other fields, and click on `Create` button

### Verify the Application
1. Click on `Test application` button
2. Click on `Application URL`
3. Verify that the Websphere-Liberty application is deployed on IBM Code Engine
4. Verify the `/health` and `/openapi` endpoints
