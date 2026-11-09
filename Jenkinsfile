pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application...'
            }
        }
stage('Deploy') {
    when {
        branch 'main'
    }
    steps {
        echo 'Deploying the application...'
    }
}            }
        
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}