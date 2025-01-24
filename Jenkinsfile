pipeline {
    agent any

    stages {
        stage('Install Apache') {
            steps {
                script {
                    echo 'Installing Apache'
                    sh 'sudo -S dnf update -y'
                    sh 'sudo -S dnf list | grep httpd'
                    sh 'sudo dnf install -y httpd.x86_64'
                    sh 'sudo systemctl start httpd.service'
                    sh 'sudo systemctl enable httpd.service'
                        }
                    }
                }

            stage ('Test index.html file') {
                steps {
                    script {
                        echo 'Test if there is syntax error in the html file'
                        sh 'sudo npm install htmlhint --save-dev'
                        sh 'sudo htmlhint /home/ec2-user/workspace/Web-Starter/index.html'
                        
                         }
                    }
                }
        
            stage('Insert index.html') {
                steps {
                    script {
                        echo 'Copy the index.html to the server'
                        sh 'sudo cp /home/ec2-user/workspace/Web-Starter/index.html /var/www/html/index.html' 
                    }
                }
            }

            stage('Test if its works') {
                steps {
                    script {
                        echo 'Test if its works'
                        sh 'sudo curl http://localhost:80'
                        }
                    }
                }
        }
}
