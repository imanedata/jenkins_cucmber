pipeline{

    agent{
        docker{
            image "cucumber/cucumber-build"
            args "--entrypoint=''"
        }
    }
     stages{
        stage('Installation node_modules'){
            steps{
                sh 'npm ci'
            }
        }
        stage('Installation node_modules'){
            steps{
                sh 'npx cypress run'
            }
        }
     }
}