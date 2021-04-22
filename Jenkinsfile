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
                
                sh 'pytest --alluredir=/reports'
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
                                results: [[path: 'target/allure-results']]
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