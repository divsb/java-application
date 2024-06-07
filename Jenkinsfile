pipeline {
    agent any
    tools{
        maven "maven397"
    }

    stages {
        stage('Clone the git repositroy') {
            steps {
                git branch: 'build-and-push-to-jfrog-jenkinsfile', credentialsId: 'githubmine', url: 'https://github.com/divsb/java-application.git'
            }
        }
        
        stage('Build the code'){
            steps {
                sh 'mvn clean install'
                
            }
        }
       
       
       stage('Push the artifacts into Jfrog artifactory') {
            steps {
              rtUpload (
                serverId: 'Jfrog-DEV-Server',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.war",
                           "target": "mydemo-app/"
                        }
                    ]
                }'''
              )
          }
        }
  
       
        
    }
}
