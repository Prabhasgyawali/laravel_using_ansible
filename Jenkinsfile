pipeline {
    agent any
     stages {
        stage('Clone Repo') {
            steps {
                git 'git@github.com:Prabhasgyawali/laravel_using_ansible.git'
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook ansibleplaybook1.yaml' // ✅ Must be inside `steps {}`
            }
        }

    }
}
