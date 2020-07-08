pipeline {
     agent any
     
     tools {
        maven 'apache-maven-3.0.1' 
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