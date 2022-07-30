properties([parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'abc', randomName: 'choice-parameter-3603878042901', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], oldScript: '', sandbox: false, script: ''], script: [classpath: [], oldScript: '', sandbox: false, script: 'return ["Prod","Dev","Test"]']]]])])

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
                   
                }
            }
        }
        stage('Confirm') {
            steps {
                script {
                
                    
                        input("Do you want to proceed building in ${user_env_input} environment?")
                
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

