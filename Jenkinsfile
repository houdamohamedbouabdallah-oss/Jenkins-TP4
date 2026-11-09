
pipeline {
    agent any

    environment {
        APP_NAME = 'Jenkins-TP4'
        DEPLOY_ENV = 'development'
    }

    stages {
        stage('Build') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Environment: ${env.DEPLOY_ENV}"
                echo "Build Number: ${env.BUILD_NUMBER}"
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
                expression {
                    env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                echo "Deploying ${env.APP_NAME} to ${env.DEPLOY_ENV}..."
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
