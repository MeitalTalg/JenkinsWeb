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
        
    }
}
