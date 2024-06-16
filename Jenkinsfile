pipeline {
    agent any
    tools{
        maven "maven397"
    }

    stages {
        stage('Clone the repository') {
            steps {
               git branch: 'build-and-deploy-to-tomcat-jenkinsfile', credentialsId: 'Github_credentails', url: 'https://github.com/divsb/java-application.git'
            }
        }
        
        stage('Build the code') {
            steps {
            sh 'mvn clean install'
                
            }
        }
        
        stage('Deploy to tomcat') {
            steps {
          deploy adapters: [tomcat9(credentialsId: 'Tomcat-9-cred', path: '', url: 'http://54.234.124.178:8080')], contextPath: null, war: '**/*.war'
                
            }
        }
    }
}
