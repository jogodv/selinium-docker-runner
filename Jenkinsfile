pipeline{
    agent none

    stages{
        
        stage('build jar'){
            agent{
                docker{
                    image: image 'maven:3.9.3-eclipse-temurin-17-focal'
                }
             }
            steps{
                sh "mvn clean package -DskipTests"
            }

        }
        stage('build image'){
            steps{
                script{
                    app= docker.build('godvindockerhub/selenium')
                }
                
                
            }
            
        }
         stage('push image'){
            steps{
                script{
                    app.push("latest")
                }
                
                
            }
            
        }
    }
}