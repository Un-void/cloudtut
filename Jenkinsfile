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

        stage('Start App Server') {
            steps {
                bat 'start /B npm run dev'
                sleep 40
            }
        }

        stage('Checkout Selenium Tests') {
            steps {
                dir('selenium-tests') {
                    git branch: 'main',
                        url: 'https://github.com/Un-void/selenium-tests.git',
                        credentialsId: 'github-token'
                }
            }
        }

        stage('Run Selenium Tests') {
            steps {
                dir('selenium-tests') {
                    bat 'mvn clean test'
                }
            }
        }

        stage('Publish Results') {
            steps {
                junit 'selenium-tests/target/surefire-reports/*.xml'
            }
        }
    }
}
