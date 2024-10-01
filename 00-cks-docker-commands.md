=================================================================================================
 # DOCKER IMAGES BUILD
=================================================================================================

# DOCKER INSTALLATION
 $ sudo apt-get install docker.io -y
 $ docker --version

# DOCKER COMMANDS
 $ sudo su
 $ cd
 $ docker --version
 $ docker images
 $ docker ps -a
 $ git clone https://github.com/azonecloud/dkr-spring-boot.git
 $ cd cc-ion-src
 $ mvn clean package
 $ nano Dockerfile
   FROM tomcat
   EXPOSE 8080
   COPY /target/ion.war /usr/local/tomat/webapps/ion.war
 $ docker build . -t ionapp
 $ docker run -p 9090:8080 ionapp
 $ docker images
 $ docker rm <container-id>
 $ docker rmi -f <image-name/id>
 $ docker stop $(docker ps -aq)
 $ docker rm $(docker ps -aq)
 $ docker rmi $(docker images -q)