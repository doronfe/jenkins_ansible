# Using the Ansible plugin on a Jenkins multi branch pipeline

Prerequisits:
Install docker https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

- Run docker daemon to start docker in the background
- Clone the folder and run from the folder: "docker compose up --build -d"
- Run: "docker ps" and search for the id of the "jenkins-main"
- Run: "docker logs <id>" and save the intial Jenkins password
- Install suggested plugins
- enter details...
- set up two nodes
- set up multi branch pipeline - use git for source and jenkinsfile for build configuration
- install ansible plugin in Jenkins
- start the job
