pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
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
                    publishHTML (target: [
				      reportDir: 'target/jacoco-report',
				      reportFiles: 'index.html',
				      reportName: "Coverage"
   					 ])
                }
            }
        }
        
    }
}