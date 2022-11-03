pipeline {
   agent any
   stages{
    stage('Git Checkout'){
      steps {
        echo 'pulling...';
         git branch:'main',
         url : 'https://github.com/benzarty/DevopsBackEnd';
         
         }
        }
    stage('testing maven'){
      steps {
        sh """mvn -version"""
         
         }
        }
       }
      }
        