pipeline {
    agent {label 'ansible'}

    environment{
        DOCKERHUB_CREDENTIALS= credentials('dockerhub-credentials')
    }
    stages{
        stage('checkout github repository'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MouhamedBechir/jenkins-ansible.git']]])
            }
        }

        stage('execute playbook'){
            steps{
                ansiblePlaybook become: true, credentialsId: 'vagrant', 
                disableHostKeyChecking: true, installation: 'ansible', 
                inventory: 'dev.inv', playbook: 'apache.yml'
            }
        }
    }
        
    }

