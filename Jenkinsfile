pipeline {
    agent any 
    stages { 
        stage('Build') {
            steps {
                echo 'Building the Project Code using Maven...'
            }
        } 
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit tests using Selenium...'
                echo 'Running Integration Tests using Apache JMeter...'
            }
            post {
                failure {
                    emailext subject: 'Unit and Integration Tests Failed', body: 'Alas! Unit and integration tests have failed. Please check the logs for details.', attachLog: true, to: 'alfithomas13@gmail.com'
                }
                success {
                    emailext subject: 'Unit and Integration Tests Succeeded', body: 'Hurray! Unit and integration tests have succeeded.', attachLog: true, to: 'alfithomas13@gmail.com'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis with SonarQube...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan with OWASP ZAP...'
            }
            post {
                failure {
                    emailext subject: 'Security Scan Failed', body: 'Alas! Security scan with OWASP ZAP has failed. Please check the logs for details.', attachLog: true, to: 'alfithomas13@gmail.com'
                }
                success {
                    emailext subject: 'Security Scan Succeeded', body: 'Hurray! Security scan with OWASP ZAP has succeeded.', attachLog: true, to: 'alfithomas13@gmail.com'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Amazon Lightsail staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on the Staging Environment'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production Server'
            }
        }
    }
}