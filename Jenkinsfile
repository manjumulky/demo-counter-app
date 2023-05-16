pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/manjumulky/demo-counter-app.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('Static code analysis'){
            
            steps{
                
                script{
                       withSonarQubeEnv(credentialsId: 'bc08ff22-96ff-424a-b814-9af8a6016d6c') {
                        
                        sh 'mvn clean package sonar:sonar'
                       }
                }
                   
            }   
                   
        }           
        stage('Quality Gate Status'){
                
            steps{
                    
                script{
                        
                    waitForQualityGate abortPipeline: false, credentialsId: '907d4867-c27b-4a37-a70a-8d33e645b880'
                    
                }
            }       
                   
        }
            
    }     
}
 

              
            
     

        
            
    


            
           
      
        
