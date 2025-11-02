pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                echo "Building Docker Image..."
                bat "docker build -t kollurichandrakala/kubesample:version1 ."
            }
        }

        stage('Docker Login') {
            steps {
                echo "Logging in to DockerHub..."
                bat 'docker login -u kollurichandrakala'
            }
        }

        stage('Push Docker Image to DockerHub') {
            steps {
                echo "Pushing Docker Image to DockerHub..."
                bat "docker push kollurichandrakala/kubesample:version1"
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Deploying to Kubernetes..."
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deployment Successful!'
        }
        failure {
            echo '❌ Build or Deployment Failed!'
        }
    }
}
