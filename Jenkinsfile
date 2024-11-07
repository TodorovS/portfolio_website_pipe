pipeline {
    agent any
    
        environment {
        IMAGE_NAME = 'todorovs/portfolio_website'
    }

    tools {
        nodejs "Node-JS-23"
        dockerTool "jenkins_docker"
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'THIS IS AN SCM CHECKOUT PLACEHOLDER'
                // checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-git', url: 'https://github.com/TodorovS/portfolio_website_pipe.git']])
            }
        }
    
        stage('Install dependencies') {
                steps {
                    echo 'THIS IS NPM INSTALL PLACEHOLDER'
                    //sh 'node -v'
                    //sh 'npm install'
                }
            }
        
        stage('Run unit test') {
                steps {
                    // sh 'npm test'
                    echo 'THIS IS A PLACEHOLDER FOR UNIT TEST'
                }
            }
            
        stage('Build Docker image') {         
                steps {
                    script {
                        my_image = docker.build("${IMAGE_NAME}")
                    }    
                }     
        }
        
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'jenkins_dockerhub') {            
                    my_image.push("${env.BUILD_NUMBER}")  // Push with build number tag
                    my_image.push("latest")               // Push with 'latest' tag
                    }
                }
            }
        }
        
        stage('Clean Workspace') {
                steps {            
                    cleanWs notFailBuild: true
                    sh 'rm -rf node_modules/*'
                    sh "docker rmi ${IMAGE_NAME}:latest ${IMAGE_NAME}:${BUILD_NUMBER}"
                }
        }       
    }
    
}