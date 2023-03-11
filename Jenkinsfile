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
                withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'passcode', usernameVariable: 'user')]) {
                sh 'docker login -u $user -p $passcode'
                }
                
                
            }
        }
    }
}
