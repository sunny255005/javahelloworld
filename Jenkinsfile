
pipeline{
    
    agent any
   
     stage("Stage1")
        {
             steps {
                 
                 script {
                    
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'Stage2\nStage3', description: '', name: 'Stage')]
                }
                sh 'echo started'
                
                
        }
        
        }
        stage("Stage2")
        {
          
              when {
                expression { myStage == 'Stage2' }
            }
       
        steps{
         
      
            
        
       // git url:"https://github.com/sunny255005/javahelloworld.git", branch:"${params.branch}"
        
      sh   "echo pulling src code from branch ${params.env}"
         script {
                    myStage = input message: 'What stage do you want to run now?', parameters: [choice(choices: 'Stage3', description: '', name: 'Stage')]
                }
            }
        
        }
        
        stage("Stage3")
        {
            
              when {
                expression { myStage == 'Stage3' }
            }
              
            steps{
                sh 'echo finish'
                
            }
        }
     
        
        }
    
        
}
