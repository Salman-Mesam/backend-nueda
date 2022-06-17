pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('test') {
            steps {
                echo 'tested!.'
            }
        }
        stage('deploy') {
            steps {
                echo 'deployed!'
            }
        }
    }
}