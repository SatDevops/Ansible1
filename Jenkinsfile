pipeline {
    agent any 
  
    stages {
     stage('Do a dry-run') {        // This will be executed only when you raise a PR
              steps {
                sh "env"   // Just to see tne environment variables as a part of the pipeline
                sh "ansible-playbook robot-dryrun.yml -e ansible_user=centos -e ansible_password=DevOps321 -e COMPONENT=mongodb -e ENV=dev"
            }
        }

}
}
