properties([parameters([string(description: '''Choose Anyone (Production OR Development or Testing) 
NOTE: All Are Case Sensitive''', name: 'env'), string(description: '''For automation USE 0 value
For not automation(manual) use any value which is non-zero''', name: 'automated')])])


properties([parameters([booleanParam(defaultValue: true, description: 'If you want to manually build', name: 'manual')])])
pipeline {
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
                        automated_value = sh (
        script: 'echo ${automated}',
        returnStdout: true
    ).trim()
                        echo "automated_value: ${automated_value}"

                    }

                //Use this value to branch to different logic if needed

                    if (automated_value != '0') {
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
