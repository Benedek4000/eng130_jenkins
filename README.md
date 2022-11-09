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

![jenkins-aws-github basic diagram](https://github.com/Benedek4000/eng130_jenkins/blob/main/images/jenkins-aws-github-basic.png)

- create a new CI/CD pipeline
- create new ssh keypair (in .ssh folder)
- use naming convention `eng130_jenkins_[name]`
- copy .pub to github repo
- copy private key to Jenkins
- create new job to test CI

![jenkins-aws-github diagram](https://github.com/Benedek4000/eng130_jenkins/blob/main/images/jenkins-aws-github.png)

### Connecting Jenkins-AWS-Github

- allow access to jenkins in the instance's security groups
- details for the CD job on jenkins:
  - source code management -> git: enter repo url, add the ssh key
  and specify branch
  - build environment -> ssh agent: add aws key (.pem)
  - build -> execute shell: enter commands, eg:

```commandline
rsync -avz -e "ssh -o StrictHostKeyChecking=no" app ubuntu@63.35.227.91:/home/ubuntu
rsync -avz -e "ssh -o StrictHostKeyChecking=no" environment ubuntu@63.35.227.91:/home/ubuntu
ssh -A -o "StrictHostKeyChecking=no" ubuntu@63.35.227.91 <<EOF
    cd app
    #bash provsion.sh
    npm install
    nohup node app.js > /dev/null 2>&1 &
EOF 
```