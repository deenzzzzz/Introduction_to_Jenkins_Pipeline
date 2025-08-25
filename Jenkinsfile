pipeline {
    agent {
        docker {
            image 'jenkins/jenkins:lts'
            args '--dns=8.8.8.8 --dns=8.8.4.4'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/deenzzzzz/Introduction_to_Jenkins_Pipeline.git'
            }
        }
        stage('Build') { steps { echo 'Building...' } }
        stage('Test') { steps { echo 'Testing...' } }
        stage('Deploy') { steps { echo 'Deploying...' } }
    }
}
