pipeline {
  agent { label 'remote-node' }
  
  stages {
    stage('Example') {
      steps {
        sh 'npm config ls'
      }
    }
    stage('Checkout') {
      steps {  
        checkout scm
      }
    }
    stage('Environment') {
      steps {  
        sh 'git --version'
        echo "Branch: ${env.BRANCH_NAME}"
        sh 'printenv'
        
      }
    }
    stage('Docker') {
      steps {   
        sh "docker-compose up -d"

       } 
    } 
    
    
  }
}