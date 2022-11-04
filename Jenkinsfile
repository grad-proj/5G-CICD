pipeline {
   agent any

   environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-grad-project')
   }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage('Login to Dockerhub') {
         steps {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
         }
      }
         
      
      stage('docker build') {
         steps {

               sh(script: """
                  cd Dockerfile/
                  make base
                  cd nf_nrf/
                  sudo docker images -a
                  sudo docker build -t gradproj/nf-nrf:latest . 
                  sudo docker images -a                  
                  cd ..
                  cd nf_pcf/
                  sudo docker build -t gradproj/pcf:latest . 
                  sudo docker images -a                  
                  cd ..
                  cd nf_nssf/
                  sudo docker build -t gradproj/nssf:latest . 
                  sudo docker images -a                  
                  cd ..
               """)
                  }
                  }
      stage('Pushing to Dockerhub') {

               steps {
                  sh 'docker push gradproj/nf-nrf:latest'
                  sh 'docker push gradproj/pcf:latest'
                  sh 'docker push gradproj/nssf:latest'
               }
            }

         }
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