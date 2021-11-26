pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_connect')
		// KUBE_CREDENTIALS=credentials('kube_config')
		// URL=serverUrl("https://ergetaks-aaf1c2e8.hcp.eastus2.azmk8s.io:443")
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t kontetsu/backend:v02 .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push kontetsu/backend:v02'
			}
		}
		// stage('kubernetes'){
		//     steps{
		//     		sh 'kubectl apply -f backend.yaml'
		//     }
		// }
		stage ('Kubernetis deploy'){
			steps {
				// withKubeCredentials([kubectlCredentials: 'KUBE_CREDENTIALS', serverUrl: 'URL']){
					sh ("/usr/local/bin/kubectl -n testenv apply -f backend.yaml")
				
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

