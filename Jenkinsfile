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
                    mkdir /home/Free5GC
                    cd /home/FreeGC
                    git clone https://github.com/free5gc/free5gc-compose
                    """)
            }
        }
        stage('Build & Dockerize') {
            steps {
                    sh(script:"""
                    #!/bin/bash
                    cd /home/Free5GC/free5gc-compose/base
                    docker build -t gradproj/base
                    """)
            }
            steps {
                    sh(script:"""
                    #!/bin/bash
                    cd /home/Free5GC/free5gc-compose/nf_ausf
                    docker build -t gradproj/nf_ausf
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
            }
            steps {
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