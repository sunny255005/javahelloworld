
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
        
        stage('Confirm for unit tests') {
                    steps {
                       script{
                           def is_unit_test_continue_parameter = input(id: 'is_unit_test_continue', message: 'Do you want to go for unit tests and jacoco reports?',

                            parameters: [[$class: 'ChoiceParameterDefinition', defaultValue: 'No',

                                description:'Unit Test choices', name:'unit tests and jacoco report', choices: 'Yes\nNo']

                            ])

                            is_unit_test_continue=is_unit_test_continue_parameter

                       }}}

                stage('Unit Tests & Jacoco Reports') {

                    when {

                 expression { is_unit_test_continue == "Yes" }

                }

             steps {

                 echo "Hello,unit_test continue...!"

                    script {

                       

                        echo 'testing in progess...'

                    }

                }

                }

                 stage('Confirm for Sonarqube Check') {

                    steps {

                       script{

                           def is_sonarqube_parameter = input(id: 'is_sonarqube', message: 'Do you want to continue with Sonarqube?',

                            parameters: [[$class: 'ChoiceParameterDefinition', defaultValue: 'No',

                                description:'Sonarqube choices', name:'sonarqube_choice_params', choices: 'Yes\nNo']

                            ])

                           is_sonarqube=is_sonarqube_parameter

                       }}}

             stage('Sonarqube Integeration') {

                    when {

                 expression { is_sonarqube == "Yes" }

             }

             steps {

                 echo "Hello,sonarqube continue...!"

                 

                }

                        }

       

        
    }
}

