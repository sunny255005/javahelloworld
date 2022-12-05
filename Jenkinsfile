
properties([parameters([choice(choices: ['Testing', 'Development', 'Production'], description: 'Choose Anyone (Production OR Development or Testing) ', name: 'env'), booleanParam(description: 'IMPORTANT NOTE : If you want to build this job manually (WITHOUT AUTOMATION) , then Please Tick The Above Button', name: 'manual')])])



pipeline{
    environment {
        PROD_BRANCH = 'master'
        STAGING_BRANCH = 'staging'
        user_env_input = 'Development'
    }

    agent any
     
   
    stages {
        stage('Which environment to build?') {
            steps {
                script {
                    script {
                        new_user_env_input = sh (
        script: 'echo ${env}',
        returnStdout: true
    ).trim()
                        echo "new_user_env_input: ${new_user_env_input}"

                        user_env_input = new_user_env_input
                        
                        
                    }

                //Use this value to branch to different logic if needed
                }
            }
        }
        stage('Confirm') {
            steps {
                script {
                    script {
                        manual_value = sh (
        script: 'echo ${manual}',
        returnStdout: true
    ).trim()
                        echo "manual_value: ${manual_value}"

                    }

                //Use this value to branch to different logic if needed

                    if (manual_value == 'true') {
                        input("Do you want to proceed building in ${user_env_input} environment?")
                    }
                }
            }
        }
        stage('Clean Build') {
            steps {
                sh 'mvn clean build'
                echo 'Building..'
            }
        }
        
        stage('Sonar Build')
        {
        withSonarQubeEnv {
    // some block
            sh './gradlew sonarqube'
}
        }

       

        
    }
}

