pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/dineshnn599-alt/Fullstack.git'
            }
        }

        stage('Build Frontend') {
            steps {
                echo 'Building frontend...'
                sh 'cd frontend && npm install && npm run build'
            }
        }

        stage('Build Backend') {
            steps {
                echo 'Building backend...'
                sh 'cd backend && npm install'
            }
        }

        stage('Restart Nginx') {
            steps {
                echo 'Restarting Nginx...'
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}

