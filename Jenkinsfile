pipeline {
    agent any
    tools {
        nodejs 'nodejs 21.7.1'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git url: "https://github.com/SomappaHittanagi/my-react-app", branch: 'main' // Replace 'main' with your branch if different
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp -r build/* ubuntu@192.168.64.5:/var/www/html/'
            }
        }
    }
}
