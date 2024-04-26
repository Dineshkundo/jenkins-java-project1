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
                googleStorageUpload bucket: 'gs://jenkins-bkt', credentialsId: 'json_key', pattern: 'target/*.war'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                //check your path carefully
                sh 'gsutil cp gs://jenkins-bkt/target/NETFLIX-1.2.2.war .'
                sh 'mv -f ./*.war /home/kundodinesh0/apache-tomcat-9.0.88/webapps'
            }
        }
    }
}
