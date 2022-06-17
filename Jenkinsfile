pipeline{
    
    agent any
	tools{
	maven 'Maven3'
	}    
    
    
    stages{
        stage("git checkout"){
            steps{
          checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sunny255005/javahelloworld.git']]])
        }
}
            stage("maven build"){
                steps{
         sh "mvn clean install"
        }
            }      
    }
}
