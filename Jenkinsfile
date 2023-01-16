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
			sh 'mvn --version'
			sh 'docker version'
		echo "Build"
		echo "$PATH"
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
			sh "mvn test"
			}
	}	
	stage('Integration Test') {
		steps {
			echo "Integration Test"
			sh "mvn failsafe:integration-test failsafe:verify"
		}
	}	
	stage('Package') {
		steps {
			echo "Package"
			sh "mvn package -DskipTests"
		}
	}		
	stage('Build Docker Image') {
		steps {
			echo "Build Docker Image"
			//docker build -t escaperadius/currency-exchange-devops:$env:BUILD_TAG
			script {
				dockerImage = docker.build("escaperadius/micro-currency-exchange:${env:BUILD_TAG}")
			}
		}
	}	
	stage('Push Docker Image') {
		steps {
			echo "Push Docker Image"
			//docker build -t escaperadius/micro-currency-exchange:$env:BUILD_TAG
			script {
				docker.withRegistry('', 'dockerHub') {
					dockerImage.push();
					dockerImage.push('latest');				
				}

			}
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
