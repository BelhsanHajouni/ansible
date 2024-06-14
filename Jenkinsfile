pipeline {
    agent any

    tools {
        ansible 'Ansible'
    }
    stages {
        stage('Git Checkout') {
            steps {
                echo 'Pulling ... '
                git branch: 'main',
                url: 'https://github.com/jasminemansouri/ansible'
            }
        }
            stage('Install Docker') {
            steps {
                script {
                    // Run the Docker role playbook
                    sh 'ansible-playbook -i hosts.ini -e "ansible_role_path=./docker" docker.yml'
                }
            }
        }
         stage('Install OpenJDK 11') {
            steps {
                script {
                    // Run the OpenJDK 11 installation playbook
                    sh 'ansible-playbook -i hosts.ini -e "ansible_role_path=./openjdk11" jdk.yml'
                }
            }
        }
    }
}
