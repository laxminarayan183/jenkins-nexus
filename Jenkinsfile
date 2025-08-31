pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/laxminarayan183/jenkins-nexus.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy Artifacts') {
            steps {
                withMaven(globalMavenSettingsConfig: 'settings.xml', jdk: 'jdk17', maven: 'maven', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn deploy'
                }
            }
        }
    }
}