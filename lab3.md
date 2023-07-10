# Lab 3 - Deploy A Back-End Java Application on IBM Code Engine
## Prerequisite - Maven
Run `mvn -v` command, if the command is not found, then Maven needs to be first installed.

On the Ubuntu VM, run the following command to install Maven.
```
sudo apt install maven
```

Run `mvn -v` command again to verify that mvn is properly installed.

## Clone the project Locally
```
git clone https://github.com/chadlouus/postgresql-jpa.git
```
Review the following files in the application to get a better idea of how the application works.

1. src/main/resources/application.properties
2. src/main/com.bezkoder.spring.jpa.postgresql.controller.TutorialController.java
3. src/main/com.bezkoder.spring.jpa.postgresql.repository.TutorialRepository.java

## Run a local build
### Create a certificate file

Create the certificate file as src/main/resources/postgres.crt
```
# Copy the certificate value from PostgreSQL environment variable
echo -n LS0tLS1C... | base64 -d > src/main/resources/postgres.crt
```
### Building a Local Docker Image

```sh
cd postgresql-jpa
# build the jar file
mvn -Dmaven.test.skip=true package
docker build -t postgresql-jpa:bootcamp .
```
## Testing the Local Docker Image
```sh
docker run --rm -p 8083:8080 --env-file env postgresql-jpa:bootcamp
```


## Verify Local Docker Container
Verify the following URLs on a browser, where `IP_ADDRESS` is the ip address of your VM, or use `localhost` if you are not using a VM
1. http://IP_ADDRESS:8083/api/tutorials

After verifying, press Ctrl-C to stop the container.

## Push Image to Container Registry and Test
```sh
docker tag postgresql-jpa:bootcamp us.icr.io/iac-cl-registry/postgresql-jpa:bootcamp
docker push us.icr.io/iac-cl-registry/postgresql-jpa:bootcamp
docker run --rm -p 8083:8080 --env-file env -d us.icr.io/iac-cl-registry/postgresql-jpa:bootcamp
curl localhost:8083/api/tutorials
```
## Deploy the Docker Image on IBM Code Engine

### Create a new Application inside the CE project
1. From your own CE project, click on `Applications` link
1. Click `Create` button
1. Enter the name of `postgresql-jpa`
1. Accept the default Container image selection
1. Under `Image reference`, enter `private.us.icr.io/ce-bootcamp-us-devN`, where `N` is your assigned developer number, such as 3
1. For `Listening port`, enter `7001`
7. For `CPU and memory`, select `0.125 vCPU / 0.25 GB`
8. Accept the default values for other fields, and click on `Create` button

### Verify the Application
1. Click on `Test application` button
2. Click on `Application URL`
3. Verify that the postgresql-jpa application is deployed on IBM Code Engine and its `/api/tutorials/` endpoint returns a correct json info
