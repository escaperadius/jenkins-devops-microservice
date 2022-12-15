pipeline {
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
	stage('Build') {
		steps {
			sh 'mvn --version'
			sh 'docker version'
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
