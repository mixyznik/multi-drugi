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
    stage('Change dir') {
      steps {   
        dir ('/home/milos/multi') {
          sh 'pwd'
          sh 'cp -R /home/milos/jenkins/workspace/multi-drugi_master/* /home/milos/multi'
          sh 'ls'
        }

       } 
    } 
    stage('Docker') {
      steps  {
         dir ('/home/milos/multi') {
          
          sh 'docker-compose up --build -d'
            }
          }
          } 
  }
}