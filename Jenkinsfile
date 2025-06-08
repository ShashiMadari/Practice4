pipeline{
	agent any
	
	environment{
		LANG='en.US_UTF-8'
		LC_ALL='en.US_UTF-8'
	}
	
	tools{
		maven 'Maven'
	}
	
	stages{
		stage('Checkout'){
			steps{
				git branch:'master', url:'https://github.com/ShashiMadari/Practice4'
			}
		}
		
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		
		stage('Artifacts'){
			steps{
				archiveArtifacts artifacts:'target/*.war',fingerprint: true
			}
		}
		
		stage('Copy WAR File'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
			}
		}
	}
}
