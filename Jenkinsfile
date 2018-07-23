pipeline{
	agent any

	parameters{
	string(name:'tomcat_dev', defaultValue:'http://192.168.56.2:8080/', description:'staging-server')
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
				sh "scp **/target/*.war vagrant@ubuntu-control:/var/lib/tomcat7/webapps"
			}
		}
	}
	
}
