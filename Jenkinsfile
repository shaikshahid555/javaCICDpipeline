
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
            }
        }

        stage('Compile') {
            steps {
                dir('HelloMaven') {
                    bat 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('HelloMaven') {
                    bat 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('HelloMaven') {
                    bat 'mvn package'
                }
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
            archiveArtifacts artifacts: 'HelloMaven/target/*.jar',
                             allowEmptyArchive: true
        }

        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
