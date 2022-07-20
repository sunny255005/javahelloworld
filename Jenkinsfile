
pipeline{
    
    agent any
   
     stage("Stage1")
        {
             steps {
                 
                 script {
                    
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'dev\nprod', description: '', name: 'Stage')]
                }
                sh 'echo started'
                
                
        }
        
        }
        stage("dev")
        {
          
              when {
                expression { myStage == 'dev' }
            }
       
        steps{
         
      
            
        
       git url:"https://github.com/sunny255005/javahelloworld.git", branch:"${params.branch}"
        
      sh   "echo pulling src code from branch ${params.env}"
         script {
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'Stage3', description: '', name: 'Stage')]
                }
            }
        
        }
        
        stage("prod")
        {
            
              when {
                expression { myStage == 'prod' }
            }
              
            steps{
                sh 'echo finish'
                
            }
        }
     
        
        }
    
        
}
