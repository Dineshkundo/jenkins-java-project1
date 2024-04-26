pipeline {
    agent any
    tools {
        maven 'maven' // Use the name configured in Jenkins
    }
    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/Dineshkundo/jenkins-java-project1.git'
            }
        }
        stage('package') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('storage') {
            steps {
              //change your required bucket details
                googleStorageUpload bucket: 'gs://jenkins-bkt', credentialsId: 'json_key', pattern: 'target/*.war'
            }
        }
    }
}
