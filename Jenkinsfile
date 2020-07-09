pipeline {
     agent any
     
     tools {
        maven 'apache-maven-3.6.3' 
     }
   
     stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'                
                }
            }
         stage('Build') {
            steps {
                sh 'docker version'
            }
        }
       } 
    }
}