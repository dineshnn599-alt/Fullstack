pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps { git branch: 'main', url: 'https://github.com/<your-username>/fullstack-app.git' }
        }
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh '''
                    npm install
                    npm run build
                    rm -rf /var/www/frontend/*
                    cp -r build/* /var/www/frontend/
                    '''
                }
            }
        }
        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh '''
                    npm install
                    pm2 delete backend || true
                    pm2 start server.js --name backend
                    '''
                }
            }
        }
        stage('Restart Nginx') {
            steps { sh 'sudo systemctl restart nginx' }
        }
    }
}