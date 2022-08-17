
properties([parameters([choice(choices: ['Testing', 'Development', 'Production'], description: 'Choose Anyone (Production OR Development or Testing) ', name: 'env'), booleanParam(description: 'IMPORTANT NOTE : If you want to build this job manually (WITHOUT AUTOMATION) , then Please Tick The Above Button', name: 'manual')])])



pipeline{
    environment {
        PROD_BRANCH = 'master'
        STAGING_BRANCH = 'staging'
        user_env_input = 'Development'
    }

    agent any
     options {
             quietPeriod(100)
            // more options
          }

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
        stage('Docker Build') {
            steps {
                echo 'Building..'
            }
        }

        stage('ECR Push') {
            steps {
                sh 'echo ECR Push'
            }
        }

        stage('Image Name Change') {
            steps {
                sh 'echo Image Name Change'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    if (user_env_input == 'Production') {
                        echo 'master branch'
                    } else if (user_env_input == 'Testing') {
                        echo 'staging branch'
                    } else {
                        echo 'dev branch'
                    }
                }
            }
        }
    }
}

