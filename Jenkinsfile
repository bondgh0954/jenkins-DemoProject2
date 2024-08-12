pipeline{
    agent any
    tools {
        maven 'maven'
    }

    stages{
        stage('build app'){
            steps{
                script{
                    echo "building app"
                }
            }
        }
        stage("deploying"){
            environment {
                AWS_ACCESS_KEY_ID = credentials('access-key-id')
                AWS_SECRET_ACCESS_KEY = credentials('secret-acess-key')
            }
            steps{
                script{
                    echo "deploying into cluster"
                    sh "kubectl create deployment nginx-deploymet --image=nginx"
                }
            }
        }
    }
}