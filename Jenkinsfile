pipeline {
   agent any
   stages {
    stage('Git Checkout') {
      steps {
        echo 'pulling...';
         git branch:'main',
         url : 'https://github.com/benzarty/DevopsBackEnd';
         
         }
        }
    stage('testing maven') {
      steps {
        sh """mvn -version"""
         
         }
        }
    stage('Test mvn') {
            steps {
              sh """ mvn -DskipTests clean package """ 
                sh """ mvn install """;
                sh """ mvn test """;
            }
        }
        
        stage('JUNIT') {
            steps {
                sh 'mvn test'
            }
        }
    stage("MVN SonarQube") {
      
          steps {
            sh "mvn sonar:sonar \
              -Dsonar.projectKey=sonarr \
              -Dsonar.host.url=http://192.168.1.21:9000 \
              -Dsonar.login=c0280cbb5b01d38ab7c54356da951f9efd900486"
      }
    }
    stage('Docker Login'){
            steps{

                sh 'docker login -u benzarty -p mohamedbenzarti'
            }
        }
    stage('Build Docker'){
            steps{
                sh 'docker build -t benzarty/devops .'
            }
        }
    stage('Nexus') {
      steps {
        sh 'mvn clean deploy -Dmaven.test.skip=true'
      }
    }

    stage('Start container') {
             steps {
                sh 'docker-compose up -d '
      }
        }
   
       }
      }
        