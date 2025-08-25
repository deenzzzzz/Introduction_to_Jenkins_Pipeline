pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // ตัวอย่างคำสั่งจริง ถ้ามี
                // sh 'python build.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // เพิ่ม delay เพื่อดูผลลัพธ์
                sleep 5
                // ตัวอย่างคำสั่งจริง ถ้ามี
                // sh 'pytest tests/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // ตัวอย่างคำสั่งจริง ถ้ามี
                // sh './deploy.sh'
            }
        }

        stage('List files') {
            steps {
                echo 'Listing files in workspace...'
                sh 'ls -l'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
