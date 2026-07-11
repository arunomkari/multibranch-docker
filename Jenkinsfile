pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 arunomkari/paytm:movie'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push arunomkari/paytm:movie'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 arunomkari/paytm:movie'
            }
        }
    }
}
