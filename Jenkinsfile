pipeline {
    agent {
       label 'master'
    }
    environment {
       BUILD_NUMBER='${env.BUILD_NUMBER}'
    }
    options {
       timesteps()
    }
    stages {
       stage('Build') {
	   sh 'docker build -t ${project_name} .'
       }
       stage('Test') {
	   sh 'npm run test'
       }
       stage('Push') {
	   sh 'docker tag'
           sh 'docker login'
           sh 'docker push'
       }
       stage('Deploy') {
           sh 'docker-compose down'
           sh 'docker-compose up -d'
       }
    }
}
