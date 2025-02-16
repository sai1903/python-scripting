pipeline {
    agent any

    environment {
        // Define any environment variables here
        PYTHON_ENV = 'venv' // Name of the virtual environment
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                // Create a virtual environment
                sh 'python3 -m venv $PYTHON_ENV'
                // Activate the virtual environment and install dependencies
                sh '''
                    source $PYTHON_ENV/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                // Activate the virtual environment and run tests
                sh '''
                    source $PYTHON_ENV/bin/activate
                    pytest tests/
                '''
            }
        }

        stage('Build') {
            steps {
                // Any build steps can go here
                echo 'Building the project...'
            }
        }
    }

    post {
        always {
            // Clean up the virtual environment
            sh 'rm -rf $PYTHON_ENV'
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
