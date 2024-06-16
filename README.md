# jenkins-DemoProject2
# Demo Project
   Create a CI pipeline with Jenkinsfile(freestyle,pipeline, Multibranch pipeline)

# Technologies Used
   Jenkins
   Docker
   Linux
   Git
   Java
   Maven

# Project Description

  CI pipeline for java Maven application to build and push to repository
      1. Install build tools(Maven, Node) in Jenkins
      2. Make Docker available on jenkins server
      3. Create Jenkins credentials for a git repository
      4. Create different Jenkins job types(freestyle, pipeline, multibranch pipeline) for the maven project with Jenkinsfile
           to connect to the application git repository
           to build jar
           to build Docker image
           to push to private DockerHub repository

# Detailed Description of steps
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

    2. Make docker available in Jenkins

      From the server where Jenkins is running
      stop the jenkins container ( docker stop containerId)
      start the container again ( docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock \
         jenkins/jenkins:lts)

      login to the running jenkins container ( docker exec -u 0 -it containerID bash)

      download docker with the curl command ( curl https://get.docker.com/ >dockerinstall && chmod 777 dockerinstall && /dockerinstall)
      grant read write permission to the '/var/run/docker.sock file' (chmod 666 /var/run/docker.sock)

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
       
       
    
      
      

        
    
    
    
    
    
