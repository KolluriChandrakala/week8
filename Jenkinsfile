pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building Docker Image: kubernetesapp"
                bat "docker build -t kubernetesapp ."
            }
        }

        stage('Run') {
            steps {
                echo "Running Docker Container from Image: kubernetesapp"
                bat "docker rm -f mycontainer || exit 0"
                bat "docker run -d -p 5000:5000 --name mycontainer kubernetesapp"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
