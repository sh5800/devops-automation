pipeline{
    agent any
    tools{
        maven 'Maven 3.9.3'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sh5800/devops-automation.git']]])
                bat 'mvn clean install'
            }
        }
        stage('Build Docker image'){
            steps{
                script{
                    bat 'docker build -t sh5800/devops-integration .'
                }
            }
        }
    }
}