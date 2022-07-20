
pipeline{
    
    agent any
   
   stages{
     stage("stage1")
        {
             steps {
                 
                 script {
                    
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'dev\nprod', description: '', name: 'Env')]
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
         
      
            
        
      
      sh   "echo pulling src code "
         script {
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'prod', description: '', name: 'env')]
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
