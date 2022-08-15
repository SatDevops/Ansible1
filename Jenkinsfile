pipeline {
    agent any 
    parameters {
         choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Chose the environment')
         string(name: 'COMPONENT', defaultValue: 'mongodb', description: 'Enter the name of the component')
    }
      environment { 
        SSH_CRED = credentials('SSH-Centos7')
       // GIT = credentials('GitHub-Token')
    }
    stages {
     stage('Do a dry-run') {        // This will be executed only when you raise a PR
              steps {
                sh "env"   // Just to see tne environment variables as a part of the pipeline
                sh "ansible-playbook robo-dryrun.yml -e ansible_user=centos -e ansible_password=DevOps321 -e COMPONENT=mongodb -e ENV=dev"
            }
        }

}
}
