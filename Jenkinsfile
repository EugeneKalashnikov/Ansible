pipeline {
    agent any
    stages {
        stage('Ansible play') {
            agent none
            steps {
                sh '''ls -la
                cd /home/jenkins/ansible
                git pull
                ansible-playbook -i hosts --extra-vars "web_ip1=172.17.0.7" --extra-vars "web_ip2=172.17.0.8" --extra-vars "web_ip3=172.17.0.9" play_role.yml
                '''
            }
        }
        stage('Testing') {
            agent none
            steps {
                sh'''curl 172.17.0.10
                curl 172.17.0.10
                curl 172.17.0.10
                '''
            } 
        }
    }
}

