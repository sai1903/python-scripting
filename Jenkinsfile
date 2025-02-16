pipeline {
    agent any  // This specifies that the pipeline can run on any available agent.

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from a Git repository
                git 'https://github.com/sai1903/python-scripting.git' // Replace with your repository URL
            }
        }

        stage('Run Python Script') {
            steps {
                // Execute the Python script
                sh 'python3 hello.py'  // Ensure Python 3 is installed on the Jenkins agent
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed!'
        }
    }
}
