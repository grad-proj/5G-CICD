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
                    git clone --mirror https://github.com/free5gc/free5gc-compose
                    """)
            }
        }
        stage('Build & Dockerize') {
            steps {
                    sh(script:"""
                    #!/bin/bash
                    cd free5gc-compose
                    docker build -t free5gc/base:latest ./base
                    cd nf_ausf
                    ls
                    docker build . -t gradproj/ausf:latest
                    """)
            }
        }
        stage('Push Container') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'Docker') {
                    sh(script:"""
                    docker tag free5gc/base:latest gradproj/base:latest
                    docker push gradproj/base:latest
                    docker push gradproj/ausf:latest
                    """)
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