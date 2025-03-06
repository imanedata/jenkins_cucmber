pipeline {
    agent {
        docker {
            image "cypress/browsers"
            args "--entrypoint=''"
        }
    }
    stages {
        stage("npm installation") {
            steps {
                sh "npm ci"
            }
        }
        stage("tests exec") {
            steps {
                sh "npx cypress run"
            }
        }
    }
    post {
        always {
            cucumber(
                jsonReportDirectory: 'cypress/cucumber-json',
                fileIncludePattern: '*.cucumber.json.json',
                buildStatus: 'UNSTABLE',
                failedFeaturesNumber: 1,
                failedScenariosNumber: 1,
                skippedStepsNumber: 1,
                failedStepsNumber: 1,
                classifications: [
                    [key: 'Commit', value: '<a href="${env.GIT_COMMIT}">${env.GIT_COMMIT}</a>'],
                    [key: 'Submitter', value: '${env.BUILD_USER}']
                ]

                reportTitle: 'My report',
                sortingMethod: 'ALPHABETICAL',
                trendsLimit: 100
            )
        }
    }
}
