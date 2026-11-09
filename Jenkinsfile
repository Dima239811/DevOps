pipeline {
    agent any

    stages {
        stage('Подготовка окружения') {
            steps {
                dir('ansible') {
                    ansiblePlaybook(
                        playbook: 'firstPlaybook.yml',
                        inventory: 'inventory/stend1/host_vars/host1',
                        credentialsId: 'ansible-ssh-key',
                        tags: 'prepare'
                    )
                }
            }
        }

        stage('Запуск приложений') {
            steps {
                dir('ansible') {
                    ansiblePlaybook(
                        playbook: 'firstPlaybook.yml',
                        inventory: 'inventory/stend1/host_vars/host1',
                        credentialsId: 'ansible-ssh-key',
                        tags: 'deploy'
                    )
                }
            }
        }
    }
}