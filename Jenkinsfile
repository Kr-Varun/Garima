
pipeline {
    agent any
    
    parameters{
        string(name: 'tomcat_stag' , defaultValue:'localhost:8090', description:'Staging-server')
        string(name:'tomcat_prod', defaultValue:'localhost:8081', description:'Production-server')
        
    }


    stages{
        stage('Build')
        {
            bat 'mvn clean package'
        }
        post{
            success{
                echo 'Now Archiving...'
                archiveArtifacts artifacts: '**/target/*.war'
            }

        }

        stage('Deployments'){
            parallel{
                stage('Deploy to Staging'){
                    steps{
                        sh "cp -i **/target/*.war C:/Users/User/Desktop/Garima_StudyMaterials/apache-tomcat-8.5.31-staging/apache-tomcat-8.5.31/webapps"
                    }
                }
                stage('Deploy to Prod'){
                    steps{
                        sh "cp -i **/target/*.war C:/Users/User/Desktop/Garima_StudyMaterials/apache-tomcat-8.5.31-prod/apache-tomcat-8.5.31/webapps"
                    }
                }

            }

        }
    }
}