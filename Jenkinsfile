pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('goraghad')
	}

	stages {

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR '
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t goraghad/dojo-jump:latest .'
			}
		}


		stage('Push') {

			steps {
				sh 'docker push goraghad/dojo-jump:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
