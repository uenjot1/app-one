pipeline {
     agent any
     
     tools {
    		maven 'mvn-3.5.2'
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