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
                
                sh 'pytest --alluredir=reports/all --json-report-file=reports/all'
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
                                results: [[path: '/allure-report']]
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