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
	     archiveArtifacts '**/*.jar, **/*.war'
               } 
          }    
     
	     stage('Email Build Status') {
		     steps {
			     mail body: '${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult} \\n\\nCheck console output at ${env.BUILD_URL} to view the results.', subject: '${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult}!!', to: 'cse1106810115@gmail.com'
		     }
	     }
     
     }   
       }
