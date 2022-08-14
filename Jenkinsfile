pipeline {
    agent any 
    parameters {
         choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Chose the environment')
         string(name: 'COMPONENT', defaultValue: 'mongodb', description: 'Enter the name of the component')
    }
    environment { 
        SSH_CRED = credentials('SSH-Cenos7')
        GIT = credentials('GitHub-Token')
    }
    stages {
     stage('Tagging') {      
            steps {
                git branch: 'main', url: "https://${GIT_USR}:${GIT_PSW}@github.com/b49-clouddevops/ansible.git"   // Git Clone
                sh "env"
                sh "bash -x auto-tag.sh"   
            }
     }
    }