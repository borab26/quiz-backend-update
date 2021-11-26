pipeline {

		agent any

		environment {
        		registry = "bora2612b/playjenkins"
        		registryCredential  = 'docker_connect'
			    dockerImage = 'playjenkins'
    		}

		stages {

			stage ('borabano - Checkout') {
				steps {
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/borab26/quiz-backend-update.git']]])
				}
			}
       stage ('Building our image') {

            steps {

                script {

                    dockerImage = docker.build registry + ":$BUILD_NUMBER"

                }

            }
        }


			stage ('Deploy our image') {
			   steps {
			       script {
			           docker.withRegistry( '', 'docker_connect') {
			       }
			   }
			}
		}

		}
		}
