pipeline {
	agent {
		docker{
			image 'node:16-bullseye-slim'
			args '-p 3000:3000'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm install'
			}
		}
		stage('Test') {
			steps {
				sh './jenkins/scripts/test.sh'
			}
		}
		stage('Manual Approval'){
			steps {
				input message: 'Lanjut ke tahap Deploy?'
			}
		}
		stage('Deploy'){ 
			steps{
				sh './jenkins/scripts/deliver.sh'
				sleep 60s
				sh './jenkins/scripts/kill.sh'
			 }
		 }	
	}
}
