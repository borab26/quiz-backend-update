pipeline {
       agent any

		environment {
        		registry = "bora2612b/bora"
        		registryCredential  = '2612bora'
			    dockerImage = 'playjenkinsback'
    		}

     stages {


	  stage ('Checkout') {
				steps {
				   script {
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/borab26/quiz-backend-update.git']]])
				}
			}
			}

       stage ('Building our image') {

            steps {

                script {

                    dockerImage = docker.build registry + ":$BUILD_NUMBER"

                }

            }
        }







      stage ('Deploy Image') {
      steps {
        script {
            dockerImage.push("playjenkinsback")


          }
        }
      }
    }
    }
