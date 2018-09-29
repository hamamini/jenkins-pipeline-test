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
		}
	}
}