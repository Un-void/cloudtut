//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
// Jenkins github-token
pipeline {
    agent any

    stages {
        stage('Checkout App') {
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

        stage('Checkout Selenium Tests') {
            steps {
                git branch: 'main',
                    url: "https://github.com/Un-void/selenium-tests.git",
                    credentialsId: 'github-token'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                bat 'mvn clean test'
            }
        }

        stage('Start App Server') {
            steps {
                bat 'npx serve -s dist -l 3000 &'
                sleep(time: 10, unit: 'SECONDS') // wait for server to start
            }
        }

        stage('Publish Results') {
            steps {
                publishTestNGResults testResultsPattern: '**/selenium-tests/target/surefire-reports/testng-results.xml'
            }
        }
    }
}
