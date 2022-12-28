pipeline {
    agent any
    stages{
        stage ('serviceinstall'){
          steps{
              sh "docker stop 22Q1"
              sh "docker rm 22Q1"
                sh "rm -rf *"
                sh " yum install git -y"
                sh "yum install docker -y"
                sh "systemctl start docker"
            }
        }
        stage ('createconatainer'){
            steps{
                sh "docker run -itd -p 90:80 --name 22Q1 httpd"
            }
        }
        stage('deploy'){
            agent{
                label{
                         label 'built-in'
                             customWorkspace "/mnt/dock"
                         }
            }
        
                             steps {    
                
                         sh "git checkout 22Q1"
                sh "chmod -R 777 /mnt/dock/index.html "
                sh "docker cp /mnt/dock/index.html 22Q1:/usr/local/apache2/htdocs"
          }
        }
    }
}
