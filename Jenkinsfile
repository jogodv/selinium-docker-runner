pipeline{
    agent any

    parameters {
        choice choices: ['chrome', 'firefox'], description: 'select browser', name: 'BROWSER'
    }

    stages{
        
        stage('Start grid'){
            
            steps{
                bat "docker-compose -f grid.yaml up --scale ${params.BROWSER}=2 -d"
            }

        }
       
         stage(''){
            steps{
                bat "docker-compose -f test-suites.yaml up"
                
            }
            
        }
    }
    post{
        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'output.flight-reservation/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'output.vendor-portal/emailable-report.html', followSymlinks: false
        }
    }
}