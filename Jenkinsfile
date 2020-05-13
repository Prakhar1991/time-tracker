pipeline{
   agent any
   tools {
             maven "Maven 3.6.3"
          }
   
     stages {
       stage('Build') {
          tools {
             maven "Maven 3.6.3"
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
