pipeline {
    agent any

    stages {
        stage('pull from japan') {
            steps {
                sh 'echo ${BRANCH_C}'
                sh 'git checkout ${BRANCH_C}'
                sh 'git merge remotes/pipline_c/${BRANCH_C}'
                sh 'git merge remotes/pipline_j/${BRANCH_J}'
                sshagent (['dwu2']) {
                sh("git push pipline_c ${BRANCH_C}:${BRANCH_C}")
                }
                sshagent (['pipline_2_2']) {
                sh("git push pipline_j ${BRANCH_C}:${BRANCH_J}")
                }            
            }
        }
        stage('Build') {
            steps {
                echo 'Building....'
                sh '/usr/sbin/httpd -v'
                sh '/usr/sbin/apachectl stop'

                sh 'ansible-playbook /etc/ansible/playbook.yml -f 10'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing....'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}