pipeline {
    agent any

    options {
        timestamps()
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                sh '''
                    mkdir -p build
                    cp index.html build/index.html
                    echo "Build completed successfully"
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application'
                sh '''
                    test -f build/index.html
                    grep -q "Welcome to My CI/CD Project" build/index.html
                    echo "All tests passed"
                '''
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline Successful!'
        }
        failure {
            echo 'CI Pipeline Failed!'
        }
    }
}
