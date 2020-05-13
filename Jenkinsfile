pipeline{
   agent any
     stages {
       stage('Build') {
          tools {
             maven: latest
          }
         steps {
              sh 'mvn clean'
              }
         }
              
       stage('Test') {
         steps {
              sh 'mvn test'
              }
        }     
       stage('Packaging') {
         steps {
              sh 'mvn package'
              }
            }
         }   
       }
