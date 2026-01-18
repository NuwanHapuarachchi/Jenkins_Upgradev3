pipeline {
    agent {
        kubernetes {
            label 'maven-agent'
            defaultContainer 'maven'
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: maven
    image: maven:3.9-eclipse-temurin-8
    command:
    - cat
    tty: true
"""
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                dir('maven-samples/single-module') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                dir('maven-samples/single-module') {
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('maven-samples/single-module') {
                    sh 'mvn package'
                }
            }
        }
    }
}
