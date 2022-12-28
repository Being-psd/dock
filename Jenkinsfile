pipeline {
    agent any
    stages{
        stage ('serviceinstall'){
            steps{
                sh "docker stop master"
                sh "docker rm master"
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
            agent{
                label{
                    label 'built-in'
                    customWorkspace "/mnt/psd"
                }
            }
                     steps{
                      
                sh "git clone https://github.com/Being-psd/dock.git"
                sh "chmod -R 777 /mnt/psd/index.html "
                sh "docker cp /mnt/psd/index.html master:/usr/local/apache2/htdocs"
                
          }
        }
    }
}
