pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_connect')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t bora2612b/backendbitch:v01 .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push bora2612b/backendbitch:v01'
			}
		}
		stage ('kube'){
			steps {
				sh ("/usr/local/bin/kubectl -n testenv apply -f backend.yaml")
				
			}
		}
	}
}

