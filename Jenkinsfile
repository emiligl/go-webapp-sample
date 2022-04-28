pipeline {
    agent any

    tools {
        go 'go-1.17'
    }

    environment {
        GO111MODULE='on'
    }

    stages {
        stage('TEST') {
            steps {
                git 'https://github.com/AdminTurnedDevOps/go-webapp-sample.git'
                sh 'go test ./...'
            }
        }

        stage('Building our image and Run') {
            steps{
                script {
                    git 'https://github.com/AdminTurnedDevOps/go-webapp-sample.git'                    
                    image = docker.build("adminturneddevops/go-webapp-sample")
                    sh "docker run -p 8090:8000 -d adminturneddevops/go-webapp-sample"
             
                }
            }
        }
    }
}
