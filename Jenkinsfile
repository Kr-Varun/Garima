pipeline{
	agent any

	parameters{
	string(name:'tomcat_dev', defaultValue:'192.168.56.2', description:'staging-server')
	}

	triggers{
		pollSCM('* * * * *')

	}
	
	stages{

		stage ('Build'){
			steps{
				sh 'mvn clean package'
				echo 'Building war file...'
				}
			post{
				success{
				echo 'Now Archiving...'
				archiveArtifacts artifacts:'**/target/*.war'
				}
			}
			}	

		stage ('Deploy to staging'){
			steps{
				sh "scp vagrant@${params.tomcat_dev}:**/target/*.war  vagrant@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
			}
		}
	}
	
}
