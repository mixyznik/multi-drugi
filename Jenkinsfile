pipeline {
  agent { label 'remote-node-new' }
  
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
          sh 'cp -R /home/milos/new/workspace/multi-drugi-new_master/* /home/milos/multi'
          sh 'ls'
        }

       } 
    } 
    stage('Docker') {
      steps  {
         dir ('/home/milos/multi') {
          sh 'docker-compose down' 
          sh 'docker system prune -f'
          sh 'docker-compose up --build -d'
            }
          }
          } 
  }    

  post{
    success{
        script{emailext(to: 'mimi.mimijevic@yandex.com', 
                        body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\nMore info at: ${env.BUILD_URL}console", 
                        recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                        subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}")}}}

  
}
