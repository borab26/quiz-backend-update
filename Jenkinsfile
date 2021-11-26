pipeline {
       agent any

		environment {
        		registry = "bora2612b/bora"
        		registryCredential  = 'docker_connect'
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

                   sh 'docker build -t bora2612b/bora:v02 .'

            }
        }

		stage('Login') {

			steps {
				sh 'echo $registryCredential_PSW | docker login -u $registryCredential_USR --password-stdin'
			}
		}





      stage ('Deploy Image') {
      steps {
        script {
            dockerImage.push("bora2612b/bora:v02")


          }
        }
      }
    }
    }
