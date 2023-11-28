pipeline {
    agent any

    // environment {
    //     ANDROID_HOME = 'C:\Program Files\Android\Android Studio\bin'
    //     GRADLE_HOME = 'C:\Users\mohci\AndroidStudioProjects\MyApplication5\.gradle'
    // }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    def gradleHome = tool 'Gradle'
                    def androidHome = tool 'Android_SDK'

                    withEnv(["PATH+GRADLE=${gradleHome}/bin",
                             "PATH+ANDROID=${androidHome}/tools",
                             "PATH+ANDROID=${androidHome}/platform-tools"]) {

                        sh './gradlew clean assembleDebug'
                    }
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    def gradleHome = tool 'Gradle'
                    def androidHome = tool 'Android_SDK'

                    withEnv(["PATH+GRADLE=${gradleHome}/bin",
                             "PATH+ANDROID=${androidHome}/tools",
                             "PATH+ANDROID=${androidHome}/platform-tools"]) {

                        sh './gradlew testDebug'
                    }
                }
            }
        }

        stage('UI Tests') {
            steps {
                script {
                    def gradleHome = tool 'Gradle'
                    def androidHome = tool 'Android_SDK'

                    withEnv(["PATH+GRADLE=${gradleHome}/bin",
                             "PATH+ANDROID=${androidHome}/tools",
                             "PATH+ANDROID=${androidHome}/platform-tools"]) {

                        sh './gradlew connectedAndroidTest'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add deployment steps if needed
            }
        }
    }

    post {
        always {
            // Clean up steps if needed
        }
        success {
            // Notification or additional steps on success
        }
        failure {
            // Notification or additional steps on failure
        }
    }
}





// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 script {
//                     echo 'Building the Android app...'
//                     sh './gradlew assembleDebug'
//                 }
//             }
//         }
        // stage('Test') {
        //     steps {
        //         script {
        //             echo 'Running tests...'
        //             sh './gradlew test'
        //         }
        //     }
        // }
//     }
// }
