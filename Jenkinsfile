
pipeline {
    agent any

    tools {
        jdk 'JDK17'
    }

    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['development', 'production'],
            description: 'Choose the deployment environment'
        )

        string(
            name: 'APP_VERSION',
            defaultValue: '1.0.0',
            description: 'Enter the application version'
        )
    }

    environment {
        APP_NAME = 'Jenkins-TP4'
    }

    stages {
        stage('Build') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Environment: ${params.DEPLOY_ENV}"
                echo "Version: ${params.APP_VERSION}"
                echo "Build Number: ${env.BUILD_NUMBER}"

                script {
                    def externalScript = load 'script.groovy'
                    externalScript.buildApp()
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def externalScript = load 'script.groovy'
                    externalScript.testApp()
                }
            }
        }

        stage('Deploy') {
            when {
                expression {
                    env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                echo "Deploying ${env.APP_NAME} version ${params.APP_VERSION} to ${params.DEPLOY_ENV}..."
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
