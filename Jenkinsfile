pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code is available in the workspace'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application'
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests'
                sh 'python3 -m unittest -v test_app.py'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application'
                sh 'tar -czf app-build.tar.gz app.py test_app.py'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: All pipeline stages completed!'
        }

        failure {
            echo 'FAILURE: Investigate the console output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
