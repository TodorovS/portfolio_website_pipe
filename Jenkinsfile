pipeline {
    agent any

    tools{
        jenkins-NodeJS-23.1
        jenkins_docker

    }

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-git', url: 'https://github.com/TodorovS/portfolio_website_pipe.git']])
            }
        }
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh 'node -v'
                sh 'npm install'
            }
        }
    }

    stages {
        stage('Run unit test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
