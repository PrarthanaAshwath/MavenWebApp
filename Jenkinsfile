pipeline {
    agent any  // Use any available agent

    tools {
        maven 'maven'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/PrarthanaAshwath/AnsibleWebApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Run Maven build
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts:'target/*.war', fingerprint:true
            }
        }

        
        
       
        stage('Deploy') {
            steps {
                sh 'mvn clean package'
                ansiblePlaybook playbook:'ansible/deploy.yml',inventory:'ansible/hosts.ini'
            }
        }

        
    }
}
