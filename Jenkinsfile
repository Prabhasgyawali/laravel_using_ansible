// pipeline {
//     agent any

//     environment {
//         COMPOSE_CMD = 'docker-compose'
//     }

//     stages {
//         stage('Clone Repo') {
//             steps {
//                 git 'git@github.com:Prabhasgyawali/sample-todo.git'
//             }
//         }

//         stage('Build & Start Containers') {
//             steps {
//                 sh "${COMPOSE_CMD} up --build -d"
//             }
//         }

//         stage('Check Running Containers') {
//             steps {
//                 sh "${COMPOSE_CMD} ps"
//             }
//         }
//     }

//     post {
//         always {
//             sh "${COMPOSE_CMD} logs || true"
//         }
//     }
// }




pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'git@github.com:Prabhasgyawali/laravel_using_ansible.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t laravel_app .'
                }
            }
        }

        stage('Push to Docker Registry') {
            steps {
                script {
                    sh 'docker tag laravel_app prabhas01/laravel_ansible:latest'
                    sh 'docker push prabhas01/laravel_ansible:latest'
                }
            }
        }

        stage('Deploy with Ansible') {
            steps {
                script {
                    sh 'ansible-playbook -i inventory laravelplaybook.yml'
                }
            }
        }
    }
}
