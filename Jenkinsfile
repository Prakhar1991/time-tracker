pipeline {
  agent any
  tools {
    maven 'mvn-latest'
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
      }      
}
