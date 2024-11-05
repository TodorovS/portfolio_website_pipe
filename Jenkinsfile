pipeline {
    agent any

    tools{
        jenkins-npm "NodeJS 23.1.0"
        jenkins_docker "latest"

    }

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-git', url: 'https://github.com/TodorovS/portfolio_website_pipe.git']])
            }
        }
    
    stage('Install dependencies') {
            steps {
                sh 'node -v'
                sh 'npm install'
            }
        }
    
    stage('Run unit test') {
            steps {
                sh 'npm test'
            }
        }
    }

}
