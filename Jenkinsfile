/*pipeline {
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
*/

pipeline {
	agent any 
		
	parameters {
		string(name: 'nginx-stg', defaultValue: '192.168.20.202', description: 'Staging')
		string(name: 'nginx-prd', defaultValue: '192.168.20.203', description: 'Live')
	}

	/*triggers {
		pollSCM('* * * * *')
	}*/

Stages {
	stage('Build'){
		steps {
			sh 'echo `date` > /Users/hamed/jenkins/index.html'
		}

		post {
			success {
				echo 'This is TEST...'
				sh 'echo `date +"%Y%m%d%H%M"` > /Users/hamed/jenkins/index.htm'
			}
		}
	}

	stage('Deployments'){
		parallel{
			stage('Deploy to Staging'){
				steps {
					sh 'scp /Users/hamed/jenkins/index.html root@$(params.nginx-stg):/var/www/html/'
				}
			}

			stage('Deploy to Live'){
				steps {
					sh 'scp /Users/hamed/jenkins/index.htm root@$(params.nginx-prd):/var/www/html/'
				}
			}
		}
	}
}
}