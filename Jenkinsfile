pipeline {
    agent any
    stages {
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('getting Free5GC ready') {
            steps {
                    sh(script:"""
                    #!/bin/bash
                    git clone https://github.com/free5gc/free5gc-compose
                    """)
            }
        }
        stage('Build & Dockerize') {
            steps {
                    sh(script:"""
                    #!/bin/bash
                    cd free5gc-compose/base
                    docker build . -t gradproj/base
                    cd ..
                    cd nf_ausf
                    docker build . -t gradproj/nf_ausf
                    """)
            }
        }
        stage('Push Container') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'DockerHub') {
                    def image = docker.build("gradproj/base:latest")
                    image.push()
                    }
                }
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'DockerHub') {
                    def image = docker.build("gradproj/nf_ausf:latest")
                    image.push()
                    }
                }
            }
        }
    }
    post{
        success{
            echo ':)'
        }
        failure{
            echo ':('
        }
    }
}