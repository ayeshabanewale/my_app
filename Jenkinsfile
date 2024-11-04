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
                 git branch: 'main', credentialsId: 'git-token', url: 'https://github.com/ayeshabanewale/my_app.git'
             }
         }  
         stage("Docker Build & Push"){
             steps{
                 script{
                    withDockerRegistry(credentialsId: '	docker-token', toolName: 'docker'){   
                        sh "docker build -t my-image ."
                        sh "docker tag my-image ayesha/swiggy-clone:latest "
                        sh "docker push ayesha/swiggy-clone:latest "
                     }
                 }
             }
         }
    }
    
} 
