properties([parameters([string('env')])])


pipeline {
    environment { 
        
        PROD_BRANCH = "master"
        STAGING_BRANCH = "staging"
        user_env_input = "Development"
       

    }
  
    agent any

    stages {
        stage('Which environment to build?') {
            steps {
                script {
                  
                     
                    user_env_input = "Production"
                   

                   sh 'echo ${env}'
                   script {
      DIR_SIZE = sh(returnStdout: true, script: " sh 'echo ${env}'")
    }

    
                   
                  
                    //Use this value to branch to different logic if needed
                }
            }
        }
        stage('Confirm') {
            steps {
                input("Do you want to proceed building in ${user_env_input} environment?")
            }
        }       
        stage('Docker Build') {
            steps {
                echo 'Building..'
                
                }
            }
        
        
        stage('ECR Push'){
            steps{
               sh 'echo ECR Push'
            }
        }

        stage('Image Name Change') {
            steps{
               sh 'echo Image Name Change'
            }
        }
        
        stage('Deploy') {
            steps{
                script {
                    if (user_env_input == "Production") {
                        echo 'master branch'
                    } else if (user_env_input == "Testing") {
                        echo 'staging branch'
                        
                    } else {
                        echo 'dev branch'
                         
                    }
                }
            }                    
        }
        
        
        
        
    }
}
