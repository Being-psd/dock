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
        stage('deploy') { 
                     steps{
                      
                sh "git pull origin 22Q1"
                sh "chmod -R 777 /root/.jenkins/workspace/docker/dock/index.html "
                sh "docker cp /root/.jenkins/workspace/docker/dock/index.html 22Q1:/usr/local/apache2/htdocs"
                
          }
        }
    }
}
