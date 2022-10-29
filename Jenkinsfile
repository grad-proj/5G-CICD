pipeline {
    agent any
    stages {
        stage('UERANSIM') {
            steps {
                parallel(
                UE: {
                    echo "This is branch a"
                },
                gNB: {
                    echo "This is branch b"
                }
                UPF: {
                    echo "This is branch b"
                }
                N3IWF: {
                    echo "This is branch b"
                }
                )
            }
        }
        stage('essential micro-services') {
            steps {
                parallel(
                AMF: {
                    echo "This is branch a"
                },
                SMF: {
                    echo "This is branch b"
                }
                )
            }
        }
        stage('UERANSIM') {
            steps {
                parallel(
                AUSF: {
                    echo "This is branch a"
                },
                NSSF: {
                    echo "This is branch b"
                }
                PCF: {
                    echo "This is branch b"
                }
                NRF: {
                    echo "This is branch b"
                }
                UDM: {
                    echo "This is branch b"
                }
                UDR: {
                    echo "This is branch b"
                }
                )
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