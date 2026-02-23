pipeline {
    agent none

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            agent any
            steps {
                git branch: 'main', url: 'https://github.com/sazo09/CI-CD-04.git' 
                stash name: 'source', includes: '**/*'
            }
        }

        stage('Compile') {
            agent {
                docker {
                    image 'gradle:6.6.1-jre14-openj9'
                }
            }
            steps {
                unstash 'source'
                dir('calculator') {
                    sh 'chmod +x ./gradlew'
                    sh './gradlew compileJava'
                }
            }
        }

        stage('Unit Tests') {
            agent {
                docker {
                    image 'gradle:6.6.1-jre14-openj9'
                }
            }
            steps {
                unstash 'source'
                dir('calculator') {
                    sh 'chmod +x ./gradlew'
                    sh './gradlew test'
                }
            }
        }
    }
}