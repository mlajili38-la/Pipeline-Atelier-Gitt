pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                // Création d'un artefact à archiver
                sh 'mkdir -p dist'
                sh 'tar -czf dist/app.tar.gz package.json test.js'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'dist/*.tar.gz', allowEmptyArchive: true
            }
        }
    }
}
