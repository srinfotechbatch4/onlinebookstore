pipeline {
    agent any

    stages {
        stage('Clone the Project') {
            steps {
               git branch: 'feature/2025.10.20', credentialsId: 'githubcredentials', url: 'https://github.com/srinfotechbatch4/onlinebookstore.git'
            }
        }

        stage('Build the Project') {
            steps {
               bat 'mvn clean install'
            }
        }

         stage('Tests') {
            steps {
               bat 'mvn test'
            }
        }

        stage('Artifact Publisher') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }

         stage('Deploy to Tomcat Server') {
            steps {
               deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcatcredetials', path: '', url: 'http://localhost:8080/')], contextPath: 'SRINFOTECHBatch4AWSAnd DevOps', war: 'target/*.war'
            }
        }
    }
}
