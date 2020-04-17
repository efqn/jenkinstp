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
				 def remote = [:]
				    remote.name = 'ansible'
				    remote.host = '192.168.56.103'
				    remote.user = 'root'
				    remote.password = 'azerty'
				    remote.allowAnyHosts = true
				    stage('Remote SSH') {
				      sshCommand remote: remote, command: "cd /home/ansible/Bureau/tpjenkins2"
				      sshCommand remote: remote, command: "playbook-ansible inventaire.ini playbook.yml"
				    }
                }
			}
		}

	}
}