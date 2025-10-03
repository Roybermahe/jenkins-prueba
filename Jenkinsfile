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

        stage('Deploy in github pages') {
            steps {
                script {
                    sh 'npm install -g angular-cli-ghpages'
                    sh 'npx angular-cli-ghpages --dir=dist/sakai-ng/browser'
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
