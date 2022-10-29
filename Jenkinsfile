pipeline {
    agent any
    stages {
        stage('UERANSIM') {
            steps {
                parallel(
                UE: {
                    echo "This is job UE"
                },
                gNB: {
                    echo "This is job gNB"
                }
                UPF: {
                    echo "This is job UPF"
                }
                N3IWF: {
                    echo "This is job N3IWF"
                }
                )
            }
        }
        stage('essential micro-services') {
            steps {
                parallel(
                AMF: {
                    echo "This is job AMF"
                },
                SMF: {
                    echo "This is job SMF"
                }
                )
            }
        }
        stage('UERANSIM') {
            steps {
                parallel(
                AUSF: {
                    echo "This is job UERANSIM"
                },
                NSSF: {
                    echo "This is job NSSF"
                }
                PCF: {
                    echo "This is job PCF"
                }
                NRF: {
                    echo "This is job NRF"
                }
                UDM: {
                    echo "This is job UDM"
                }
                UDR: {
                    echo "This is job UDR"
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
