pipeline {
    agent any
    stages {
        stage('Clean Workspace'){
            steps{
                cleanWs()
             }
         }
         stage('Checkout from Git'){
             steps{
                 git branch: 'main', url: 'https://github.com/Ashfaque-9x/a-swiggy-clone.git'
             }
         }  
         stage("Docker Build & Push"){
             steps{
                 script{
                    withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker'){   
                        sh "docker build -t swiggy-clone ."
                        sh "docker tag swiggy-clone ashfaque9x/swiggy-clone:latest "
                        sh "docker push ashfaque9x/swiggy-clone:latest "
                     }
                 }
             }
         }
    }
