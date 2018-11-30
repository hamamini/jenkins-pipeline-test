pipeline {
	agent any
	stages {
		stage('Init'){
			steps {
				echo "Testing...."
			}
		}

		stage('Build'){
			steps {
				echo 'Building....'
			}
		}

		stage('Deploy'){
			steps {
				echo 'Code Deployed.'
			}
		}
		stage('var_test'){
			steps {
				build job: 'var_test'
			}
			post {
				success {
					echo 'Success'
				}
				failure {
					echo 'Failure'
				}
		}
		stage('usr_test'){
			steps {
				timeout(time:5, unit:'DAYS'){
					input message:'Approve usr_test Build?'
				}
				build job: 'usr_test'
			}
			post {
				success {
					echo 'Success'
				}
				failure {
					echo 'Failure'
				}
			}
		}
	}
}