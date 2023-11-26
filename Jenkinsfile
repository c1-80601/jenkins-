pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/c1-80601/jenkins-.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_ZpaCWumdUSl9RU6rVM_fapH70k4 | /usr/bin/docker login -u pratik234 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t pratik234/jenkins2 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push pratik234/jenkins2'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 pratik234/jenkins2'
            }
        }
    }
}
