pipeline {
	agent any
	stages {
	stage('Build') {
		steps {
		echo "Build"
		}
	}
	stage('Test') {
				steps {
		echo "Test"
				}
	}	
	stage('Deploy') {
				steps {
		echo "Deploy"
				}
	}	
	} 

	post {
		always {
			echo "I'm awesome I run always"
		}
		success {
			echo "I run when you are successful"
		}
		failure {
			echo "I run when you are a failure"
		}		
	}

}
