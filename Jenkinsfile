pipeline {
   agent any
   enviroment{
    DOCKERHUB_CREDENTIALS = credentials(dockerhub-grad-project)
   }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage('SCM Checkout')
        steps{
            git 'https://github.com/grad-proj/5G-CICD.git'
        }

        stage('docker build') {
            steps {

                sh(script: """
                    cd Dockerfile/nf-nrf
                    docker images -a
                    docker build -t gradproj/nrf:1.0.0 . 
                    docker images -a                  
                    cd ..
                """)
                }




//       stage('Ueransim') {
//          parallel {
//             stage('Run gnb') {
//                steps {
//                   echo "command"

//                }
//             }
//             stage('Run ue') {
//                steps {
//                   echo "command"
//                }
//             }
//          }
//          }





//       stage('Free5gc') {
//          parallel {
//             stage('Run free5gc-amf') {
//                steps {
//                   echo "command"

//                }
//             }
//             stage('Run free5gc-smf') {
//                steps {
//                   echo "command"
//                }
//             }
//          }
//          }




//       stage('Free5gc-2') {
//          parallel {
//             stage('Run free5gc-ausf') {
//                steps {
//                   echo "command"

//                }
//             }
//             stage('Run free5gc-nssf') {
//                steps {
//                   echo "command"
//                }
//             }
//             stage('Run free5gc-pcf') {
//                steps {
//                   echo "command"
//                }
//             }
//             stage('Run free5gc-nrf') {
//                steps {
//                   echo "command"
//                }
//             }
//             stage('Run free5gc-udm') {
//                steps {
//                   echo "command"
//                }
//             }
//             stage('Run free5gc-udr') {
//                steps {
//                   echo "command"
//                }
//             }
//          }
//          }


//     }
//     }