pipeline{
    agent any

    stages{
        
        stage('RUN TEST'){
            
            steps{
                bat "docker-compose up"
            }

        }
       
         stage('BRING GRID DOWN'){
            steps{
                bat "docker-compose down"
                
            }
            
        }
    }
}