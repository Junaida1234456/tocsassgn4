pipeline {
    agent any
    
    stages {
        stage('Run Docker Compose') {
            steps {
                script {
                    // Clone git submodule
                    sh 'git submodule update --init --recursive'

                    // Run Docker Compose without sudo
                    sh 'docker-compose -f index.html up -d --build'
                }
            }
        }  
    }
}

