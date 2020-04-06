# refactor-udagram-app
This project was a part of my Cloud Developer Nanodegree by Udacity.

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

<h2><b>Tasks</b></h2>
<h4>Setup Docker Environment<h4>

You'll need to install docker https://docs.docker.com/install/. 
Open a new terminal within the project directory and run:

1. Switch the folder: <code>cd udacity-c3-deployment/docker</code>
2. Build the images: <code>docker-compose -f docker-compose-build.yaml build --parallel</code>
3. Push the images: <code>docker-compose -f docker-compose-build.yaml push</code>
4. Run the container: <code>docker-compose up</code>

<h4>Setup k8s Environment</h4>
1. Create the cluster: <code>eksctl create cluster --name udagram</code>
2. Create travis-user: <code>eksctl create iamidentitymapping --name udagram --role <Your_Role_ARN> --group system:masters --username <Your_Username></code>
3. Run the ci/cd-pipeline
