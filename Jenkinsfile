pipeline {
    agent any

    environment {
        ENV1 = "value1"
    }

    stages {
        stage('Build') {
            agent {
                docker {
                 image 'node:18-alpine'   
                 reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                 image 'node:18-alpine'   
                 reuseNode true
                }
            }
            steps {
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
        stage('Deploy') {
            
            steps {
                sh '''
                    echo "Inside Deploy"
                    echo "Environment Name : $ENV1"
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
