
# Dockerized Jenkins & Sonar combo

This is the Dockerized solution I' am working on, first as a way of learning to navigate Docker and second, as a way to learn how to setup the whole enchilada of Continuous Integration.

## Requirements

 * Docker Engine 17.06.0+
 * Docker Compose 1.13.0

## Running it

Use [docker-compose](https://github.com/docker/compose) to start the containers.

```bash
$ docker-compose up
```

## Jenkins

Pre installed plugins:
 * SonarQube 2.6.1
 * Bitbucket 1.1.5

### First run

During the initial run of Jenkins a security token is generated and printed in the console log:

```
*************************************************************

Jenkins initial setup is required. A security token is required to proceed.
Please use the following security token to proceed to installation:

41d2b60b0e4cb5bf2025d33b21cb

*************************************************************
```

 This token must be entered in the "Setup Wizard" the first time you open the Jenkins UI(_host-machine-ip:8080_). This token will also serve as the default password for the user admin if you skip the user-creation step in the Setup Wizard.

### Configuring BitBucket webhooks

After Jenkins is set up:
1. Create a project on Jenkins
1. Open the projects configuration page
1. Under `Source code management`, select git and configure access to your repo
1. Under `Build Triggers`, mark the checkbox `Build when a change is pushed to BitBucket`

On BitBucket:
1. Open your repo settings on BitBucket
1. Under `Integrations`, click on the link `Webhooks`
1. Add a webhook with title "Jenkins" and URL as "http://<host machine ip>:8080/bitbucket-hook/"
1. Make sure the status is marked as "Active"

### Configuring SonarQube

Once you have configured SonarQube itself.

To-Do: Finish this section.

## SonarQube

### Install a code analyzer

Go to `Administration > System > Update Center`, select `Available` and search for *SonarJava*, or whatever lame language you program.

### Generate a Key

Click over your name and then on *My account*, go to *Security*, enter a token name and click on generate. Save the token, you won't be able to see the token again later.
