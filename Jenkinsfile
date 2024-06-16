pipeline{
  agent any
  tools{
    maven 'maven-3'
  }

  stages{
    stage('build jar'){
      steps{
        script{
          echo 'building jar file for the application'
          sh 'mvn package'
        }
      }

    }
    stage('build Image'){
      steps{
        script{
          echo 'building application image'
          sh 'docker build -t nanaot/java-app:newp.1 .'
          withCredentials([usernamePassword(credentialId:'dockerhub-credentials',usernameVariable:'USER',passwordVariable:'PASS')]){
            sh "echo $PASS |docker login -u $USER --password-stdin"
            sh 'docker push nanaot/java-app:newp.1'
          }
        }
      }
    }

  }
}