pipeline{
   agent any
    
    tools{
     maven 'Maven'
     }
     
     
     stages{
       stage('Checkout'){
        steps{
         git branch :'master',url: 'https://github.com/shraddha1231/web'
         }
        }
        
         stage('Build'){
        steps{
         sh 'mvn clean package'
         }
        }
        
         stage('Archive'){
        steps{
         archiveArtifacts artifats = 'target/*.war', fingerprint = true
         }
        }
        
         stage('Deeploy'){
        steps{
         sh 'ansible-playbook playbook.yml -i hosts.ini'
         }
        }
        }
     post{
     success{
     echo 'build'
     }
     failure{
     echo 'fail'
     }
     }
     }
