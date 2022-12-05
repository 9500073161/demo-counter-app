pipeline{

    tools{
        jdk 'Java'
        maven 'mymaven'
    }
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/9500073161/demo-counter-app.git'
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
        
       stage('upload war file to nexus'){
                
                steps{
                    
                    script{
                        
                        nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/springboot-1.0.0.jar', type: 'jar']], credentialsId: 'nexus-auth', groupId: 'com.example', nexusUrl: '3.83.40.232:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'demo-release', version: '1.0.0'
                    }
                }
            }       
     
        
        }
        
}
