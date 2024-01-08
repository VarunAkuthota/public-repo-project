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
                if (isUnix()) {
					withMaven(maven: 'Maven-3.6.3-Linux') {
						sh 'mvn clean package -DskipTests'
					}
				} else {
					withMaven(maven: 'Maven-3.6.3') {
						bat 'mvn clean package -DskipTests'
					}
				}
            }
        }
 
        stage('Test') {
            steps {
                // Runnings tests
                if (isUnix()) {
					withMaven(maven: 'Maven-3.6.3-Linux') {
						sh 'mvn test'
					}
				} else {
					withMaven(maven: 'Maven-3.6.3') {
						bat 'mvn test'
					}
				}
            }
        }
 
        // Additional stages like 'Deploy' can be added here if necessary
 
    }
}
