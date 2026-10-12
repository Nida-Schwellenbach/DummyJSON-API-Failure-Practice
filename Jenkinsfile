
pipeline {
    agent any

    stages {
        stage('Run API Tests') {
            steps {
                bat '''
                    newman run "DummyJSON_API_Failure_Practice.postman_collection.json" -e "postman_environment.json" -r cli,htmlextra --reporter-htmlextra-export "newman-report.html"
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
