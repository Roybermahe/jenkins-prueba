pipeline {
    agent any

    environment {
        IMAGE_NAME = "angular-sakai"
        CONTAINER_NAME = "angular-sakai-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Roybermahe/jenkins-prueba.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        /* stage('Run Tests') {
            steps {
                script {
                    sh 'npm run test --watch=false --browsers=ChromeHeadless'
                }
            }
        } */

        stage('Build Angular') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finalizado"
        }
    }
}
