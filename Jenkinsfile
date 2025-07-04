pipeline {
    agent any

    environment {
        INVENTORY = 'inventory/aws_single_node.ini'
        PLAYBOOK = 'site.yml'
        SSH_KEY_ID = 'ansible_ssh'
    }

    stages {
        stage('Checkout Ansible Code') {
            steps{
                url: 'https://github.com/AnilVishwanathAvhad/ansible-3tier-deploy.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    sudo apt update || sudo yum update -y
                    sudo apt install -y python3-pip || sudo yum install -y python3-pip
                    pip3 install --user ansible
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sshagent(credentials: [env.SSH_KEY_ID]) {
                    sh """
                        ansible-playbook -i ${INVENTORY} ${PLAYBOOK} \
                        --extra-vars "env=dev"
                    """
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment completed successfully!'
        }
        failure {
            echo '❌ Deployment failed. Please check logs.'
        }
    }
}

    
