<h1>Jenkins-DemoProject2</h1>
Create a CI pipeline with Jenkinsfile(freestyle,pipeline, Multibranch pipeline)

<h2>Project Description</h2>
 Create CI pipeline for java Maven application to build and push to artifact repository<br/>
      1. Install build tools(Maven, Node) in Jenkins<br/>
      2. Make Docker available on jenkins server<br/>
      3. Create Jenkins credentials for a git repository<br/>
      4. Create different Jenkins job types(freestyle, pipeline, multibranch pipeline)<br/>
         for the maven project with Jenkinsfile to connect to the application git repository<br/>
           - to build jar
           - to build Docker image
           - to push to private DockerHub repository
 
<br />


<h2>Technologies used</h2> 
- <b>Jenkins</b> <br/>
- <b>Docker</b> <br/>
- <b>Git</b> <br/>
- <b>Linux</b> <br/>
- <b>Maven</b><br/>
- <b>Java</b><br/>

<h2>Detailed Description of Project </h2>

<p align="center">
  1. Install build tools (Maven and node) in jenkins
    from the jenkins UI go to 'manage jenkins'
    tools 
    maven installateion

    Installation of node inside the jenkins container
    login to jenkins container as root user (docker exec -u 0 -it containerId bash)
    update the binaries ( apt update)
    install curl (apt install curl)
    download node with the curl command (curl -sl https://deb.nodesource.com/setup_20.x -o nodesource_setup.sh)
    run the script (bash nodesource_setup.sh)
    install node (apt-get install nodejs -y)

    from the UI of jenkins go to 'manage jenkins'
    go to plugins
    download nodjs
    install nodejs plugin from tools in the jenkins UI
  <img src='./screenshots/image.png' height="80%" width="80%" alt="Disk Sanitization Steps">

  2. install docker on the server <br/>
     Set up and run jenkins as Docker container<br/>
     ssh into the server (ssh root@publicIP)<br/>
     update the binaries (apt update)<br/>
     install docker (apt install docker.io)
  <img src='./screenshots/2image.png' height="80%" width="80%" alt="Disk Sanitization Steps">
  <img src='./screenshots/3image.png' height="80%" width="80%" alt="Disk Sanitization Steps">

  3. install Jenkins as docker image<br/>
   docker ps<br/>
   login to the jenkins running container (docker exec -it containerId bash)<br/>
   configure firewall custom port and add jenkins container port 8080<br/>
   enter the publicIp of the jenkins server and the port where jenkins is running into the browser<br/>
   (publicIp:port)<br/>
   get the content of the password for jenkins<br/>
   install plugins<br/>
  <img src='./screenshots/4image.png' height="80%" width="80%" alt="Disk Sanitization Steps">

  
    Jenkins image has been pulled from dockerhub and the container is running as well
   <img src='./screenshots/6image.png' height="80%" width="80%" alt="Disk Sanitization Steps">

   2.  Make docker available in Jenkins

      From the server where Jenkins is running
      stop the jenkins container ( docker stop containerId)
      start the container again ( docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock \
         jenkins/jenkins:lts)

      login to the running jenkins container ( docker exec -u 0 -it containerID bash)

      download docker with the curl command ( curl https://get.docker.com/ >dockerinstall && chmod 777 dockerinstall && /dockerinstall)
      grant read write permission to the '/var/run/docker.sock file' (chmod 666 /var/run/docker.sock)
   <img src='./screenshots/image.png' height="80%" width="80%" alt="Disk Sanitization Steps">

    3. Create Jenkins credentials for the git repository
       source code management in jenkins UI
       select Git
       copy the code from github repository
       paste inside repository url

       create credentials for the repository in Jenkins
       enter the user name and password of github or gitlab repository

 4. Create different Jenkins job types(freestyle, pipeline, multibranch pipeline) for the maven project with Jenkinsfile
           to connect to the application git repository
           to build jar
           to build Docker image
           to push to private DockerHub repository

      i. Create a freestyle job in jenkins
      Jenkins Dashboard
      New Item
      freestyle job

      2. Create pipeline job in jenkins
         add jenkins file to the application repository

         Jenkins file

         build jar file ( mvn package)
         build docker image ( docker build -t name + tag)
         push image to docker hub repository ( docker push name+tag)

   

</p>

 
           

