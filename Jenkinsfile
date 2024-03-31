pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    sh 'docker build -t tKite/python-flask-docker .'
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/*.jar', allowEmptyArchive: true // Архивируем результат сборки
        }
    }
}
