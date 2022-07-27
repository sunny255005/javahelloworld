properties([parameters([string('env')])])
properties([parameters([string('automated')])])
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

                        automated_value = sh (
        script: 'echo ${automated}',
        returnStdout: true
    ).trim()
                        echo "automated value: ${automated_value}"
                    }

                //Use this value to branch to different logic if needed
                }
            }
        }
        stage('Confirm') {
            steps {
                script {
                    if (user_env_input != new_user_env_input) {
                        input("Do you want to proceed building in ${user_env_input} environment?")
                    }
                else {
                        sh 'echo going to  next stages'
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
