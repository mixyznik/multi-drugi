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
        dir ('/home/mixy/multi') {
          sh 'pwd'
          sh 'cp -R /home/milos/jenkins /home/mixy/multi/'
          sh 'ls'
        }

       } 
    } 

    stage('Docker') {
      steps  {
        dir ('/home/mixy/multi')  {
          sh 'docker-compose down'
          sh 'docker system prune -f'
          sh 'docker-compose up --build -d'
            }
          
            }

       } 
  }
}