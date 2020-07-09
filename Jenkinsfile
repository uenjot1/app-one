pipeline {
     agent any
     
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
                sh 'docker build -t uenjot/app-one .'
            }
        } 
        
        
         stage('info-end') {
            steps {
                sh 'ls -l'
            }
        }
     }
   
     
}