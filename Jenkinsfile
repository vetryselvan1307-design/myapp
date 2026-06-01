pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/vetryselvan1307-design/myapp.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true

                docker run -d \
                  --name myapp \
                  -p 80:80 \
                  myapp:latest
                '''
            }
        }
    }
}
