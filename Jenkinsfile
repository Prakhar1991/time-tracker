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
        stage('Consolidate results') {
          steps {
             input("Do you want to store the results?")
             junit '**/target/surefire-reports/TEST-*.xml'
				 archive 'target/*.jar'
               } 
          }    
     
     
     
     }   
       }
