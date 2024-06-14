pipeline {
    agent any
    tools{
        maven "maven397"
    }

    stages {
        stage('Clone the Repository ') {
            steps {
               git branch: 'static-code-analysis-jenkinsfile', credentialsId: 'Github_credentails', url: 'https://github.com/divsb/java-application.git'
               
               
            }
        }
        
        stage('Build the maven code') {
            steps {
                sh 'mvn clean install'
           }
        }    
        
        stage('Static code analysis') {
            steps {
        withSonarQubeEnv('Sonarqube-8.9.10') {
                    sh  "mvn sonar:sonar"
                }
                }
                
            }
        
        
    }
}
