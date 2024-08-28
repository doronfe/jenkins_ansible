# pipelines

Comments:
- This Readme is incomplete
- Used Dockerfiles from the course repositories as is
- I'm cloning the git repository in each secondary pipeline, 
  I need to do that only once in the main one...
- Docker build doesn't work because the docker daemon is not running
  I think I need to use a "script" with docker.build in order for that to work

Prerequisits:
Install ngrok: https://dashboard.ngrok.com/get-started/setup/linux
Install docker https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

Trigger the main pipeline with:
curl -X POST "https://4c33-77-126-13-88.ngrok-free.app/job/main_pipeline/build" --user admin:11f63051f95e49fd7bbe967a39644f9eaa

replace https://4c33-77-126-13-88.ngrok-free.app with the jenkins host address
