pipeline {
    agent any
    stages{
        stage ('serviceinstall'){
            steps{
                sh "rm -rf *"
                sh " yum install git -y"
                sh "yum install docker -y"
                sh "systemctl start docker"
            }
        }
        stage ('createconatainer'){
            steps{
                sh "docker run -itd -p 80:80 --name master httpd"
            }
        }
        stage('deploy') { 
                     steps{
                      
                sh "git clone https://github.com/Being-psd/dock.git"
                sh "chmod -R 777 /root/.jenkins/workspace/docker/dock/index.html "
                sh "docker cp /root/.jenkins/workspace/docker/dock/index.html master:/usr/local/apache2/htdocs"
                
          }
        }
    }
}
