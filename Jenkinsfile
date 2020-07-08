pipeline {
     agent any
   
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