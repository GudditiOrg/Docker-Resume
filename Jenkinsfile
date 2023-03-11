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
                withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                    sh "docker login --username ${DOCKERHUB_USERNAME} --password ${DOCKERHUB_PASSWORD}"
                    sh "docker build -t gudditi/tomcat-resume:latest ."
                    sh "docker push gudditi/tomcat-resume:latest"
            }
        }
    }
}
