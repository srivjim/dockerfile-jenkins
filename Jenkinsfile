pipeline{
  agent { label 'vps-ssh' }

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub_id')
	}

	stages {
		stage('Build') {

			steps {
				sh 'sudo docker build -t apacheraul/apacheraul:latest .'
			}
		}

		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {
			steps {
				sh 'sudo docker tag apacheraul/apacheraul:latest'
				sh 'sudo docker push apacheraul/apacheraul:latest'
			}
		}
	}

	post {
		always {
			sh 'sudo docker logout'
		}
	}

}
