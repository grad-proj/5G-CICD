pipeline {
    agent any
    stages {
        stage('Verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        // stage('getting Free5GC ready') {
        //     steps {
        //             sh(script:"""
        //             #!/bin/bash
        //             git clone https://github.com/free5gc/free5gc-compose
        //             """)
        //     }
        // }
        stage('Build & Dockerize') {
            steps {
                    sh(script:"""
                    #!/bin/bash
                    cd free5gc-compose
                    docker build -t free5gc/base:latest ./base
                    cd nf_ausf
                    ls
                    docker build . -t gradproj/nf_ausf:latest
                    """)
            }
        }
        stage('Push Container') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'Docker') {
                    def image = "gradproj/nf_ausf:latest"
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