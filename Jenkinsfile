pipeline {
    agent any

    stages {
        stage('with docker') {
            agent {
                docker {
                 image 'node:18-alpine'   
                 reuseNode true
                }
            }
            steps {
                sh 'echo "with docker"'
                sh 'npm --version'
            }
        }
    }
}
