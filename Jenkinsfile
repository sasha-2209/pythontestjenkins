pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sasha-2209/pythontestjenkins.git']]])
            }
        }
        stage('Build') {
            steps {
                browserstack(credentialsId: 'eb97920c-6104-4e74-84f2-da6d80e409c6') 
                git branch: 'main', url: 'https://github.com/sasha-2209/pythontestjenkins.git'
                sh 'python3 test.py'
            }
        }
        stage('Test') {
            steps {
                browserstack(credentialsId: 'eb97920c-6104-4e74-84f2-da6d80e409c6') 
                sh 'python3 -m pytest'
            }
        }
    }
}
