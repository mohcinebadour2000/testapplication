pipeline {
    agent any
    
    environment {
        ANDROID_HOME = 'C:\Users\mohci\AppData\Local\Android\Sdk'
        PATH = "${env.PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools"
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out your code from version control
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build your Android application
                sh './gradlew clean assembleDebug'
            }
        }

        stage('Test') {
            steps {
                // Run your tests, you might need to customize this depending on your testing framework
                sh './gradlew testDebug'
            }
        }

        stage('Deploy') {
            steps {
                // You can add deployment steps here if needed
            }
        }
    }

    post {
        always {
            // Clean up or perform any final tasks here
        }

        success {
            // Actions to be taken if the pipeline is successful
        }

        failure {
            // Actions to be taken if the pipeline fails
        }
    }
}
