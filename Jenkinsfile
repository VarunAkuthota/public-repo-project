pipeline {
    agent any

    tools {
        // Ensure these tool versions are available in your Jenkins configuration
        maven 'Maven-3.6.3' // Replace with your Maven version
        jdk 'JDK-11' // Replace with your JDK version
    }

    stages {
        stage('Checkout') {
            steps {
                // Checking out source code from Git
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Building the project with Maven
                withMaven(maven: 'Maven-3.6.3') {
                    script {
                        if (isUnix()) {
                            sh 'mvn clean package'
                        } else {
                            bat 'mvn clean package'
                        }
                    }
                }
            }
        }

        stage('Test') {
            steps {
                // Running tests
                withMaven(maven: 'Maven-3.6.3') {
                    script {
                        if (isUnix()) {
                            sh 'mvn test'
                        } else {
                            bat 'mvn test'
                        }
                    }
                }
            }
        }

        // Additional stages like 'Deploy' can be added here if necessary
    }
}
