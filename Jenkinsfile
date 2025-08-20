pipeline {
    agent {label 'ec2-agent'}
    environment {
        GITHUB_TOKEN=credentials('GitHub-pat')
    }

    tools {
        allure 'allure' 
    }
    
    stages {
        stage('build') {
            steps {
                sh 'mvn clean test'
            }
        }

             stage('Allure Report') {
            steps {
                allure([
                    includeProperties: false,
                    jdk: '',
                    results: [[path: 'target/allure-results']] 
                ])
            }
        }
    }
}
