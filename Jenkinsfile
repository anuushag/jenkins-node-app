pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git branch: 'main' , url: 'https://github.com/anuushag/jenkins-node-app.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t jenkins-node-app .'
      }
    }

    stage('Run App in Container') {
      steps {
        sh 'docker run -d -p 3000:3000 --name jenkins-node-app jenkins-node-app'
      }
    }
  }
}
