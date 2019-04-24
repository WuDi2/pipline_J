pipeline {
    agent any

    stages {
        stage('pull from japan') {
            steps {
                bat 'echo %BRANCH_C%'
                bat 'git checkout %BRANCH_C%'
                bat 'git merge remotes/pipline_c/%BRANCH_C%'
                bat 'git merge remotes/pipline_j/%BRANCH_J% --allow-unrelated-histories'
                sshagent (['dwu2']) {
                bat("git push pipline_c %BRANCH_C%:%BRANCH_C%")
                }
                sshagent (['pipline_2_2']) {
                bat("git push pipline_j %BRANCH_C%:%BRANCH_J%")
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