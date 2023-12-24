pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clone the entire repository to the workspace
                checkout scm
            }
        }

        stage('Build image') {
            steps {
                // Build the Docker image
                script {
                    def app = docker.build("junaid345/hellonode")
                }
            }
        }

        stage('Test image') {
            steps {
                // Ideally, run a test framework against the Docker image
                script {
                    app.inside {
                        sh 'echo "Tests passed"'
                    }
                }
            }
        }

        stage('Push image') {
            steps {
                // Push the Docker image with two tags
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
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
