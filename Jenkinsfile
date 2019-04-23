pipeline {
    agent any

    stages {
        stage('pull from japan') {
            steps {
            	bat 'echo %BRANCH_C%'
                bat 'git checkout %BRANCH_C%'
                bat 'git merge remotes/pipline_test2_1/%BRANCH_C%'
                bat 'git merge remotes/pipline_test2_2/%BRANCH_J%'
                sshagent (credentials: ['dwu2']) {
                bat("git push pipline_test2_1 %BRANCH_C%:%BRANCH_C%")
                }
                sshagent (credentials: ['pipline_2_2']) {
                bat("git push pipline_test2_1 %BRANCH_C%:%BRANCH_J%")
                }            
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