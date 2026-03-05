pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/sahithya0586/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t node-docker-app:${BUILD_NUMBER} .
                '''
            }
        }

       
        
        stage('Create container') {
            steps {
                sh 'docker run -d -p 3000:8080 node-docker-app:${BUILD_NUMBER}'
            }
        }



    }
}
