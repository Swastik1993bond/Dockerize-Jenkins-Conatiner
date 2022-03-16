# Dockerize-Jenkins-Conatiner

How to run the coantainer:

keep this files in your local/server and run the shell script:

sh jenkins-Docker.sh

This will setup the image and create the container in port 8080 and 50000 for controller

Accessing the Docker container
If you have some experience with Docker and you wish or need to access your Docker container through a terminal/command prompt using the docker exec command, you can add an option like --name jenkins-tutorial to the docker exec command. That will access the Jenkins Docker container named "jenkins-tutorial".
This means you could access your docker container (through a separate terminal/command prompt window) with a docker exec command like:

 docker ps 
 
 docker exec -it <Conatainer name> bash

Accessing the Docker logs
There is a possibility you may need to access the Jenkins console log, for instance, when Unlocking Jenkins as part of the Post-installation setup wizard.
The Jenkins console log is easily accessible through the terminal/command prompt window from which you executed the docker run …​ command. In case if needed you can also access the Jenkins console log through the Docker logs of your container using the following command:

 docker logs <docker-container-name>

Your <docker-container-name> can be obtained using the docker ps command. Accessing the Jenkins home directory
There is a possibility you may need to access the Jenkins home directory, for instance, to check the details of a Jenkins build in the workspace subdirectory.

If you mapped the Jenkins home directory (/var/jenkins_home) to one on your machine’s local file system (i.e. in the docker run …​ command above), then you can access the contents of this directory through your machine’s usual terminal/command prompt.
Otherwise, if you specified the --volume jenkins-data:/var/jenkins_home option in the docker run …​ command, you can access the contents of the Jenkins home directory through your container’s terminal/command prompt using the docker container exec command:

 docker container exec -it <docker-container-name> bash

As mentioned above, your <docker-container-name> can be obtained using the docker container ls command. If you specified the
--name jenkins-blueocean option in the docker container run …​command above (see also Accessing the Jenkins/Blue Ocean Docker container), you can simply use the docker container exec command:

 docker container exec -it jenkins-blueocean bash
 
 The command: sudo cat /var/lib/jenkins/secrets/initialAdminPassword will print the password at console.
If you are running Jenkins in Docker using the official jenkins/jenkins image you can use :

sudo docker exec ${CONTAINER_ID or CONTAINER_NAME} cat /var/jenkins_home/secrets/initialAdminPassword 
   to print the password in the console without having to exec into the container.
