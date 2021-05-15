pipeline {
	agent any

	stages 
	{
		stage('unit Test') {
			steps {
				echo 'unit Testing..'
			}
		}

		stage('Build') {
			steps {
				echo 'Building..'
			}
		}
		stage('Test') {
			steps {
				echo 'Testing..'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying....'
			}
		}

		stage('mobile') {
			environment { 
				MOBILE_BUILD = 'true'
			}
			steps {
				dir('mobile') {
					script {


						try {
							def strCount = sh(returnStdout: true, script: "git diff --name-only ${env.GIT_COMMIT} ${GIT_PREVIOUS_SUCCESSFUL_COMMIT} | grep mobile | wc -l").trim()
							if(strCount=="0") {
								MOBILE_BUILD="false"
								echo "SKIP mobile"
							}
						}
						catch (error) {

						}

						if(MOBILE_BUILD=='true'){
							echo "Changes found in mobile"
							echo 'build for mobile'
							sh 'echo 123'
						}


					}



				}


			}
		}

		stage('web') {
			steps {
				echo 'build for web'
			}
		}


	}
}