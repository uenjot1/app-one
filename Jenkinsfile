pipeline {
     agent any
     
     stages {
        stage('Build') {
            steps {
            withMaven(maven : 'apache-maven-3.6.3') {
				sh 'mvn -B -DskipTests clean package'
				}            
            }
        }
        stage('Test') { 
            steps {
            withMaven(maven : 'apache-maven-3.6.3') {
			    sh 'mvn test' 
				}            
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'                
                }
            }
         }
         stage('Docker') {
            steps {
                sh 'docker version'
            }
        } 
    }
}