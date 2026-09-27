# Tomcat Multi-Environment CI/CD

This project implements a CI/CD pipeline to automatically build and deploy a Java web application to multiple Apache Tomcat environments using GitHub Actions.

## Project Architecture

GitHub Repository
        |
        v
GitHub Actions
        |
        v
Maven Build
        |
        v
WAR File
        |
        v
Environment Selection
        |
   +----+----+---------+
   |    |    |         |
  DEV  TEST PRE-PROD  PROD
   |    |    |         |
 Tomcat Tomcat Tomcat Tomcat
   |    |    |         |
   +----+----+---------+
        |
        v
Application Deployment

## Technologies Used

- AWS EC2
- Apache Tomcat
- Java JDK 17
- Maven
- Git
- GitHub
- GitHub Actions
- Linux/Ubuntu

## Environments

The application can be deployed to:

- DEV
- TEST
- PRE-PROD
- PROD

The required environment is selected from the GitHub Actions workflow dropdown.

## CI/CD Pipeline

The GitHub Actions workflow performs the following steps:

1. Checkout source code
2. Setup Java JDK
3. Maven Validate
4. Maven Compile
5. Maven Test
6. Maven Package
7. Generate WAR file
8. Deploy WAR file to the selected Tomcat server

## Tomcat Configuration

Apache Tomcat was installed and configured on AWS EC2 instances.

Tomcat Manager was configured with the required user and roles to allow automated deployment through the Tomcat Manager API.

## GitHub Secrets

Environment-specific secrets are configured in GitHub:

- TOMCAT_HOST`
- TOMCAT_USER`
- TOMCAT_PASSWORD`

These secrets are used by GitHub Actions during deployment.

## Deployment

The workflow can be manually triggered from:

GitHub → Actions → CI/CD Pipeline to Deploy to Tomcat → Run Workflow

Select the required environment:

- DEV
- TEST
- PRE-PROD
- PROD

The WAR file is then deployed automatically to the selected Tomcat server.

## Application URL

After deployment, the application can be accessed using:

http://<EC2-PUBLIC-IP>:8080/TrainBook

## Project Structure

text
tomcat-multi-env-cicd/
│
├── src/
├── WebContent/
├── pom.xml
├── README.md
│
└── .github/
    └── workflows/
        └── cicd.yaml
