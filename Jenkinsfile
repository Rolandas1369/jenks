pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                
                sh 'pytest --alluredir=reports --json-report-file=reports/all'
            }
        }
        stage('reports') {
            steps {
                script {
                        allure([
                                includeProperties: false,
                                jdk: '',
                                properties: [],
                                reportBuildPolicy: 'ALWAYS',
                                results: [[path: 'reports/all']]
                        ])
                }
            }
}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}