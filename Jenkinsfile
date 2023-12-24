pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Junaida1234456/tocsassgn4'  // Replace with your repository URL
            }
        }

        stage('Build Image') {
            steps {
                script {
                    dockerImage = docker.build("junaid345/spaceimage")  // Replace with your Docker Hub username and image name
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
