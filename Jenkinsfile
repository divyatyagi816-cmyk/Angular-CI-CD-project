pipeline {
    agent any

    tools {
        NodeJS Plugin
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/divyatyagi816-cmyk/Angular-CI-CD-project.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build -- --configuration production'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test -- --watch=false --browsers=ChromeHeadless'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                aws s3 sync dist/ci-cd-demo/browser/ s3://angular-ci-cd-demo-divya-816 --delete
                '''
            }
        }
    }
}