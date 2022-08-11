pipeline {
    agent any

    stages {
        stage('Dry run') {
            steps {
                sh "ansible-playbook -i inventory -u centos -e ansible_password=DevOps321 -e COMPONENT=frontend -e ENV=dev roboshop.yml"
            }
        }
        
    }
}