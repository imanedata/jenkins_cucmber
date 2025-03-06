pipeline {
    agent {
        docker {
            image 'cypress/browsers'
            args '--entrypoint=""'
        }
    }
    
    stages {
        stage('Installation node_modules') {
            steps {
                sh 'npm ci'
            }
        }
        
        stage('Run Cypress') {
            steps {
                sh 'npx cypress run'
            }
        }
    }
}

