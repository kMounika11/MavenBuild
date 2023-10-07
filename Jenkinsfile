pipeline {
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    
    stages {
         stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post{
                success {
                    echo "Archiving the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
            
        }
        stage ('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'b6277120-f038-45d5-b338-592685d7e549', path: '', url: 'http://localhost:8081/')], contextPath: null, war: '**/*.war'
            } 
        }
    }
}
	
	
