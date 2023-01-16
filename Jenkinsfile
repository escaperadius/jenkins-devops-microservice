pipeline {
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}	
	stages {
		stage('Checkout') {
			steps {
				echo "Checkout"				
				sh 'mvn --version'
				sh 'docker version'

				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"		
				echo "BUILD_TAG - $env.BUILD_TAG"			
			}
		}
		stage('Compile') {
			steps {
				echo "Compile"
				sh "mvn clean compile"
				}
		}			
		stage('Test') {
			steps {
				echo "Test"
				sh 'mvn test'				

			}
		}		
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
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
