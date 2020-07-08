pipeline {
     agent any
     
     tools {
        maven 'apache-maven-3.6.3' 
     }
   
     stages {        
          stage("Mvn") {
               steps {
                    sh "mvn -version"
               }
          }
          stage("Docker") {
               steps {
                    sh "docker version"
               }
          }
     }
}