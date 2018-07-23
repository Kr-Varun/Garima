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
				echo 'Hello World!'
				}
			}	
		}
	
}
