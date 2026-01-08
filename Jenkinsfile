pipeline {
    agent any
    stages {
        stage('Start') {
            steps { echo "Starting pipeline..." }
        }
        stage('Clone repository') {
            steps {
                git url: 'https://github.com/<your-username>/jenkins-demo.git', branch: 'main'
                echo "Repository cloned."
            }
        }
        stage('Verify index.html') {
            steps {
                script {
                    if (fileExists('index.html')) {
                        echo "index.html found."
                    } else {
                        error "index.html is missing!"
                    }
                }
            }
        }
        stage('Report success') {
            steps { echo "All checks passed." }
        }
    }
    post {
        success { echo "Build SUCCESS." }
        failure { echo "Build FAILURE. Check logs." }
        always { echo "Pipeline finished." }
    }
}
