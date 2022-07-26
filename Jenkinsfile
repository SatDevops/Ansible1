pipeline {
    agent any 
    parameters {
         choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Chose the environment')
         string(name: 'COMPONENT', defaultValue: 'mongodb', description: 'Enter the name of the component')
    }
    environment { 
        SSH_CRED = credentials('SSH-Centos7')
        GIT = credentials('Github-token')
    }
    stages {
        
        stage('Lint Checks') {  // This will be executed against the feature branch only
            when { branch pattern: "feature-.*", comparator: "REGEXP"}
            steps {
                sh "env"
                sh "echo Style Checks"
                sh "echo running is feature branch"
            }
        } 

        stage('Do a dry-run') {        // This will be executed only when you raise a PR
             when { branch pattern: "PR-.*", comparator: "REGEXP"}
            steps {
                sh "env"   // Just to see tne environment variables as a part of the pipeline
                sh "ansible-playbook robot-dryrun.yml -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW} -e COMPONENT=${params.COMPONENT} -e ENV=${params.ENV}"
            }
        }

        stage('Tagging') {
            when { branch 'main' }       
            steps {
                git branch: 'main', url: "https://${GIT_USR}:${GIT_PSW}@github.com/SatDevops/Ansible1.git"   // Git Clone
                // sh "env"
                sh "bash -x auto-tag.sh"   
            }
        }

    //     stage('Running On Tag') {          // This will run when we push a tag
    //         when { 
    //            expression { env.TAG_NAME != null }
    //             }       
    //         steps {
    //             sh "echo Runs only when you push a git tag"
    //         }
    //     }
    // }
}
}
