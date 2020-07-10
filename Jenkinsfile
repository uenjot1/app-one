pipeline {
     agent any
     
      environment {
	    registryCredential = 'DOCKER_HUB'
	    dockerImage = ''
  	}
     
     tools {
        maven 'apache-maven-3.6.3' 
     }
     
      stages {
        stage('info-start') {
            steps {
                sh 'ls -l'
            }
        }
        
         stage('Build') {
            steps {
                sh 'mvn -B -DskipTests -Dmaven.repo.local=/var/jenkins_home/workspace/unj1/m2 clean package'
            }
        }
         stage('Test') { 
            steps {
                sh 'mvn -Dmaven.repo.local=/var/jenkins_home/workspace/unj1/m2  test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'                
                }
            }
         } 
         stage('Docker') {
            steps {
				  script{
				  	def dockerImage = docker.build("uenjot/app-one:${env.BUILD_ID}")           		
				  }
				  sh 'docker images'         	
            }
        } 
         stage('Docker push') {
            steps {
             script{
	                docker.withRegistry( '', registryCredential ) {
	            	dockerImage.push()
          		}
          		}
            }
        } 
        
        
         stage('info-end') {
            steps {
                sh 'ls -l'
            }
        }
     }
   
     
}