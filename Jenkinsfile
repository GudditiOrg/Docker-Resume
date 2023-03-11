pipeline {
    agent any
    stages {
        stage ('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GudditiOrg/Docker-Resume.git'
            }

        }
        stage ('mvn build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('docker build and push'){
            steps {
                sh 'docker build -t gudditi/tomcat-resume:latest .'
            }
        }
    }
}
