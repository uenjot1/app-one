pipeline {
     agent any
   
     stages {        
          stage("Mvn") {
          	agent {
       			 docker {
            		image 'maven:3-alpine'
           		    args '-v $HOME/.m2:/root/.m2'
        		}
    		}
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