	pipeline{

		agent any

		environment {
        		registry = "bora2612b/bora"
        		registryCredential  = '2612bora'
			    dockerImage = 'playjenkinsback'
    		}



            
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
        }


			stage ('Deploy our image') {
			   steps {
			       script {
			           docker.withRegistry( '', '2612bora') {
			       }
			   }
			}
		}

      stage ('Deploy Image') {
      steps {
        script {
          docker.withRegistry( '', '2612bora' ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')

          }
        }
      }
    }
           
           
           
           }
