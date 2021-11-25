	pipeline {

		agent any

		environment {
        		registry = "bora2612b/bora"
        		registryCredential  = 'bora2612b'
			    dockerImage = 'playjenkins'
    		}

		stages {

			stage ('borabano - Checkout') {
				steps {
						checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/borab26/quiz-backend-update.git']]])
				}
			}
			stage ('Building our image') {
				steps {
				   script {
                       dockerImage = docker.build registry + ":$BUILD_NUMBER"
				   }
				}

			stage('Deploy our image') {
			   steps {
			       script {
			           docker.withRegistry( '', bora2612b) {
			       }
			   }
			}
		}

		}
	}
	}
