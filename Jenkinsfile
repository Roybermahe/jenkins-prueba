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

        stage('Run Tests') {
            steps {
                script {
                    sh 'npm run test -- --watch=false --browsers=ChromeHeadless'
                }
            }
        }

        stage('Build Angular Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f $CONTAINER_NAME || true'
                    sh 'docker run -d --name $CONTAINER_NAME -p 4201:4200 $IMAGE_NAME'
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
