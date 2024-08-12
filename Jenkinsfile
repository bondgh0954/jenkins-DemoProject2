pipeline{
    angent any
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
            steps{
                script{
                    echo "deploying into cluster"
                }
            }
        }
    }
}