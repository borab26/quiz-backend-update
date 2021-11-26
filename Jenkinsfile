pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_connect')
		// KUBE_CREDENTIALS=credentials('kubebora')
		// URL=serverUrl("https://boradns-k8s-77357fd6.hcp.switzerlandnorth.azmk8s.io:443")

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
	    stage ('Kubernetis deploy'){
			steps {
				sh ("kubectl apply -f backend.yaml")
			}
		}
	}
}

