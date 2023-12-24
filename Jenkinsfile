pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clone the entire repository to the workspace
                sh 'git clone https://github.com/Junaida1234456/tocsassgn4 .'
            }
        }

        stage('Build image') {
            steps {
                // Build the Docker image
                app = docker.build("getintodevops/hellonode")
            }
        }

        stage('Test image') {
            steps {
                // Ideally, run a test framework against the Docker image
                app.inside {
                    sh 'echo "Tests passed"'
                }
            }
        }

        stage('Push image') {
            steps {
                // Push the Docker image with two tags
                docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
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
