pipeline {
    agent any

    stages {
        stage('Pull data form git') {
            steps {
                
                git branch: 'master', url: 'https://github.com/rithika9191/jenkins'
            }
        }

        stage('Build Image') {
            steps {
                sh 'ls -l'
                
                sh 'docker build -t iamrithika/myweb1 .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                
                sh 'echo "dckr_pat_5OoZK-OYItQ2To81WSgQC2QJS5U" | docker login -u iamrithika --password-stdin'
            }
        
        }

        stage('push image') {
            steps {
                
                sh 'docker push iamrithika/myweb1'
            }
        }

        stage('remove existing service') {
            steps {
                
                sh 'docker service rm myservice'
            }
        }

        stage('create service') {
            steps {
                sh 'docker service create --name myservice -p 4000:4000 --replicas 2 iamrithika/myweb1'
            }
        }
    }
}
