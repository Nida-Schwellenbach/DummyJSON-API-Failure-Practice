
pipeline {
    agent any

    environment {
        COLLECTION = 'DummyJSON_API_Failure_Practice.postman_collection.json'
        ENVIRONMENT = 'postman_environment.json'
        REPORT = 'newman-report.html'
    }

    stages {
        stage('Run API Tests with Newman') {
            steps {
                bat '''
                    newman run "%COLLECTION%" -e "%ENVIRONMENT%" -r cli,htmlextra --reporter-htmlextra-export "%REPORT%"
                '''
            }
        }
    }

    post {
        always {
            publishHTML([
                reportDir: '',
                reportFiles: 'newman-report.html',
                reportName: 'Newman API Failure Practice Report',
                keepAll: true,
                alwaysLinkToLastBuild: true,
                allowMissing: false
            ])
        }
    }
}
