# Jenkins

## CI/CD

- CI: continuous integration
- CD: continuous delivery or continuous deployment
- CE: continuous exploration

![cicd pipeline diagram](https://github.com/Benedek4000/jenkins/blob/main/images/cicd%20pipeline.png)

### CD vs CD

In continuous delivery, most of the process is automated to simplify 
deployment, while in continuous deployment, the whole process is automated.

### Webhook

A webhook is an HTTP-based callback function allowing simple communication
between 2 APIs.

## Jenkins

Jenkins is a CI/CD automation software widely used by DevOps engineers.

### Benefits

- open source
- cloud hosting
- free
- available on Windows, Linux and macOS

### Stages

Jenkins lets the user create different tasks to be a part of the pipeline.
Jenkins then will execute this pipeline when necessary, performing the tasks
in order. These tasks are stored in the `Jenkinsfile` in a format similar 
to JSON.

### Companies using Jenkins

- Facebook
- Netflix
- Udemy
- etc

### Other tools

- Bamboo
- Gitlab
- CircleCI
- TeamCity
- Buddy
- TravisCI
- etc

## Instructions

- create a new CI/CD pipeline
- create new ssh keypair (in .ssh folder)
- use naming convention `eng130_jenkins_[name]`
- copy .pub to github repo
- copy private key to Jenkins
- create new job to test CI