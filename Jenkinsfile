pipeline {
    agent any

    stages {
        stage('Checkout Tests') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Un-void/cloudtut.git',
                    credentialsId: 'github-token'
            }
        }

        stage('Install') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                bat 'echo Deploying React app...'
            }
        }

        stage('Checkout Tests') {
            steps {
                git branch: 'main', url: 'https://github.com/your-org/selenium-tests.git'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                bat 'mvn clean test'
            }
        }

        stage('Publish Results') {
            steps {
                publishTestNGResults testResultsPattern: '**/target/surefire-reports/testng-results.xml'
            }
        }
    }
}
