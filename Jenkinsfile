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
		string(name: 'nginx_stg', defaultValue: '192.168.20.202', description: 'Staging')
		string(name: 'nginx_prd', defaultValue: '192.168.20.203', description: 'Live')
	}

	/*triggers {
		pollSCM('* * * * *')
	}*/

stages {
	stage('Build'){
		steps {
			sh 'echo `date` > /var/jenkins_home/index.html'
		}

		post {
			success {
				echo 'This is TEST...'
				sh 'echo `date +"%Y%m%d%H%M"` > /var/jenkins_home/index.htm'
			}
		}
	}

	stage('Deployments'){
		parallel{
			stage('Deploy to Staging'){
				steps {
					echo "${params.nginx_stg}"
					/*sh "scp /var/jenkins_home/index.html root@${params.nginx_stg}:/var/www/html/"
				}
			}

			stage('Deploy to Live'){
				steps {
					sh "scp /var/jenkins_home/index.htm root@${params.nginx-prd}:/var/www/html/"*/
				}
			}
		}
	}
}
}