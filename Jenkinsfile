pipeline {
  agent any
  tools {
    maven "Maven 3.6.3"
  }
    
    stages { 
     stage("Parallel Execution") {
			steps {
				parallel(
				      a: {
					bat "mvn clean"
				      },
				      b: {
					bat "mvn test"
				      },
				      c: {
					bat "mvn package"
				      }
				)
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
