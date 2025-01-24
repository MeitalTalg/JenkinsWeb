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
            stage('Insert index.html') {
                steps {
                    script {
                        echo 'Copy the index.html to the server'
                        sh 'sudo mv /home/ec2-user/workspace/Web-Starter/index.html /var/www/html/index.html' 
                }
            }
        }

                stage('Test') {
                steps {
                    script {
                        echo 'Test if its works'
                        sh 'sudo curl http://localhost:80'
                }
            }
        }

        
    }
}
