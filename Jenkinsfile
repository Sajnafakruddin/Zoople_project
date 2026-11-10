pipeline {
    agent none

    stages {
        stage('build') {
            agent {
                label 'buildnode'
            }
            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/Sajnafakruddin/Zoople_project.git
                    ls -la
                '''

                stash name: 'webpage', includes: 'Zoople_project/**'
            }
        }

        stage('deploy') {
            agent {
                label 'deploynode'
            }
            steps {
                deleteDir()

                unstash 'webpage'

                sh '''
                    rm -rf /var/www/html/*
                    cp -r Zoople_project/* /var/www/html/
                    ls -la /var/www/html/
                '''
            }
        }
    }
}
