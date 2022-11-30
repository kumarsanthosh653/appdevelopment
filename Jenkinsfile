pipeline{

	agent any

        environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-id')
	}

	stages {
               
		stage('Build') {

			steps {
				sh 'docker build -t santhosh/app:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push santhosh/app:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
