pipeline {
    agent any

    tools {
        jdk 'jdk-8'
        maven 'maven-3.9'
    }

    stages {

        stage('Init') {
            steps {
                echo 'Starting Maven CI Pipeline'
            }
        }

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

        stage('Deploy (Staging)') {
            steps {
                echo 'Deploying JAR to staging (placeholder)'
            }
        }

        stage('Deploy (Production)') {
            steps {
                echo 'Deploying JAR to production (manual gate later)'
            }
        }
    }
}
