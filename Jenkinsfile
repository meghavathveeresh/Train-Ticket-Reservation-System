pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'github', url: 'https://github.com/meghavathveeresh/Train-Ticket-Reservation-System.git'
            }
        }
          stage('Build') {
            steps {
               bat 'mvn clean install'
            }
        }
          stage('Generate Artifacts') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
		stage('Deploy to Tomcat Server') {
        steps {
            deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'AMDN', path: '', url: 'http://localhost:8080')], contextPath: 'MV TRAIN SERVICE', war: 'target/*.war'
        }
    }
    }
}
