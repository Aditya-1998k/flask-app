pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      git 'https://github.com/Aditya-1998k/flask-app.git'
    }

    stage('Build Docker Image') {
      steps {
        sh 'eval $(minikube docker-env)'
        sh 'docker build -t flask-hello .'
      }
    }

    stage('Deploy with Ansible') {
      steps {
        sh 'ansible-playbook -i ansible/inventory.ini ansible/deploy.yml'
      }
    }
  }
}
