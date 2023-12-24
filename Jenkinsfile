pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'spaceimage'  // Replace with your Docker image name
        GITHUB_REPO_URL = 'https://github.com/Junaida1234456/tocsassgn4'  // Replace with your GitHub repository URL
        TARGET_PORT = '2555'
    }

    stages {
        stage('Build and Containerize') {
            steps {
                script {
                    // Clone the GitHub repository inside the Docker container
                    docker.image('alpine/git:latest').inside {
                        sh "git clone ${GITHUB_REPO_URL} /app"
                    }

                    // Build and containerize the files in the cloned directory
                    docker.image(DOCKER_IMAGE).inside("-v /app:/build") {
                        sh 'ls -la /build'  // Placeholder for build commands, adjust as needed
                        // Add your build commands here

                        // For example, if using Python:
                        // sh 'python3 -m http.server ${TARGET_PORT} --bind 0.0.0.0 --cgi &'
                    }
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
