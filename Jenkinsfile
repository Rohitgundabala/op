pipeline {
    agent any

    environment {
        GIT_URL = 'https://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@github.com/Rohitgundabala/rohitpriv.git'
    }

    stages {
        stage("Clone Repository") {
            steps {
                script {
                    deleteDir()
                    git url: GIT_URL
                }
            }
        }

         stage("docker image build"){
            steps{
                script{
                    sh 'docker build -t gundabalarohit2104/rohitpro1 .'
                }
            }
        }
        stage("docker image push"){
            steps{
                script{
                    sh 'docker login -u gundabalarohit2104 -p 1319@Rohit'
                    sh 'docker push gundabalarohit2104/rohitpro1'
                }
            }
        }
        stage("docker run"){
            steps{
                script{
                    if (sh(script: 'docker ps -q -f name=rcont1', returnStatus: true) == 0) {
                        sh 'docker stop rcont1 || true'
                        sh 'docker rm rcont1 || true'
                    }
                    sh 'docker run -d --name web -p 8083:80 gundabalarohit2104/rohitpro1'
                }
            }
        }
    }
}
