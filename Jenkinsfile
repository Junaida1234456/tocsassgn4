pipeline {
    agent any
    
    stages {
        stage('Run HTTP Server') {
            steps {
                script {
                    // Clone git submodule
                    sh 'git submodule update --init --recursive'

                    // Start a simple HTTP server
                    sh 'python3 -m http.server 8000 &'

                    // Sleep for a few seconds to allow the server to start
                    sleep(time: 10, unit: 'SECONDS')
                }
            }
        }  
    }
}
