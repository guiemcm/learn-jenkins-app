pipeline {
    agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "Running BUILD stage ..."
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage("Test"){
            steps{
                sh '''
                    echo "Running TEST stage ..."
                    test -f "build/index.html"
                    npm test
                '''
            }
        }
    }
}