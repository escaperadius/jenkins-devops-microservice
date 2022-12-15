pipeline {
	agent any
	stages {
	stage('Build') {
		echo "Build"
	}
	stage('Test') {
		echo "Test"
	}	
	stage('Deploy') {
		echo "Deploy"
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
