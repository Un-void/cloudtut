pipeline {
    agent any

    tools {
        // Define tools configured in Jenkins Global Tool Configuration
        nodejs 'Node_16'
        maven 'Maven_3.8.1'
        jdk 'Java_11'
    }

    stages {
        stage('Checkout App') {
            steps {
                git branch: 'main', url: 'https://github.com/your-org/react-app.git'
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
                // Replace with your actual deployment steps
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
