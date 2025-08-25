pipeline {
    agent any

    parameters {
        booleanParam(name: 'RUN_DEPLOY', defaultValue: true, description: 'Should we deploy?')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Select deployment environment')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'echo "Build successful" > build.log'
            }
        }

        stage('Test in Parallel') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        echo 'Running unit tests...'
                        sh 'sleep 5'
                        sh 'echo "Unit tests passed" > unit_results.txt'
                        archiveArtifacts artifacts: 'unit_results.txt', fingerprint: true
                    }
                }
                stage('Integration Tests') {
                    steps {
                        echo 'Running integration tests...'
                        sh 'sleep 5'
                        sh 'echo "Integration tests passed" > integration_results.txt'
                        archiveArtifacts artifacts: 'integration_results.txt', fingerprint: true
                    }
                }
                stage('Simulate Linux Tests') {
                    steps {
                        echo 'Simulating tests on Linux...'
                        sh 'sleep 3'
                    }
                }
                stage('Simulate Windows Tests') {
                    steps {
                        echo 'Simulating tests on Windows...'
                        sh 'sleep 3'
                    }
                }
            }
        }

        stage('Approval') {
            options {
                timeout(time: 2, unit: 'MINUTES') // Auto-fail if no approval
            }
            steps {
                input message: "Do you want to proceed with deployment?"
            }
        }

        stage('Deploy') {
            when {
                expression { return params.RUN_DEPLOY }
            }
            steps {
                echo "Deploying application to ${params.ENVIRONMENT} environment..."
                sh 'echo "Deployment complete" > deploy.log'
                archiveArtifacts artifacts: 'deploy.log', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check logs!'
        }
        always {
            echo 'Pipeline completed (success or failure).'
        }
    }
}
