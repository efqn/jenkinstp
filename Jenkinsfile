pipeline {
	agent {
		docker {
			image 'node:6-alpine'
		}
	}
	environment {
	CI = 'true'
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm install'
			}
		}
		// stage('Test') {
		// 	steps {
		// 		sh 'npm test'
		// 	}
		// }
		stage('ansible playbook') {
			steps{
				ansiblePlaybook (
					colorized: true,
					become: true,
					playbook: 'playbook.yml'
				)
			}
		}

	}
}