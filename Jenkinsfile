pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/NicolasPascal/repo-fork.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to server...'
                // Tambahkan skrip deploy nyata di sini (scp, Docker push, dll.)
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
