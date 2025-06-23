pipeline {
    agent any
    environment {
        REMOTE_USER = 'apache'
        REMOTE_HOST = '10.121.7.133'
        SSH_KEY_ID = 'apache-ssh-key'
        WEB_ROOT = '/var/www/html/webroot/ROOT' // Adjust if different
    }
    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Add Directory') {
            steps {
                sh '''
                    mkdir -p milan
                '''
            }
        }
        stage('Debug workspace') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }
    }
}
