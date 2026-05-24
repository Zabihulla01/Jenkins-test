pipeline {
    agent any

    environment {
        DOCKER = credentials('Docker')
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Zabihulla01/Jenkins-test.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t zabihulla01/p1:latest .'
            }
        }

        stage('Docker Login') {
            steps {
                sh '''
                echo $DOCKER_PSW | docker login \
                -u $DOCKER_USR \
                --password-stdin
                '''
            }
        }

        stage('Push DockerHub') {
            steps {
                sh 'docker push zabihulla01/p1:latest'
            }
        }
       stage('run docker image'){
          steps{
            sh 'docker run -d -p 80:80 --name abc zabihulla01/p1:latest'
          }
        } 

    }
}
