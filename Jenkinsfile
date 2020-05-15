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
      
      
      }      
}
