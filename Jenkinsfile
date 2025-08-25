pipeline {
    agent { label 'master' }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/deenzzzzz/Introduction_to_Jenkins_Pipeline.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
