pipeline {
  agent any
  tools {
    maven "Maven 3.6.3"
  }
    
    stages { 
      stage('Build') {
         steps {
            sh 'echo "running the maven goal clean"'
            sh 'mvn clean'  
            }
           }
           
       stage('test') {
          steps {
            sh 'echo "Runnning maven test stage"'
            sh 'mvn -e test'
            }
           }
        
       stage('Archiving Packages') {
          steps {
             sh 'echo "packaging the artifacts"'
             sh 'mvn package'
             }
            } 
      
      stage('Consolidate results') {
          steps {
             input("Do you want to store the results?")
             junit '**/target/surefire-reports/*.xml'
	           archiveArtifacts '**/*.jar, **/*.war'
               } 
          }   
	    
      stage('Email Build Status') {
          steps {
		  mail body: '${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult} \\n\\nCheck console output at ${env.BUILD_URL} to view the results.', subject: '${env.JOB_NAME}  - Build # ${env.BUILD_NUMBER}  - ${currentBuild.currentResult}!!', to: 'cse1106818@gmail.com'
		     }
	     }	    
      
      
      }      
}
