pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-git', url: 'https://github.com/TodorovS/portfolio_website_pipe.git']])
            }
        }
    }
}
