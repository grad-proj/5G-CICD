pipeline {
   agent any


environment {
    DOCKERHUB_CREDENTIALS=credentials('Docker_hub_pro')
   }
   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
//
//
//
//
 //     stage('Ueransim') {
 //        parallel {
 //           stage('Run gnb') {
 //              steps {
 //                 echo "command"
//
 //              }
 //           }
 //           stage('Run ue') {
 //              steps {
 //                 echo "command"
 //             }
 //           }
 //        }
 //        }
 //



//
 //     stage('Free5gc') {
 //        parallel {
 //           stage('Run free5gc-amf') {
 //              steps {
 //                 echo "command"
//
 //              }
 //           }
 //           stage('Run free5gc-smf') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //        }
 //        }
//
//
//
//
 //     stage('Free5gc-2') {
 //        parallel {
 //           stage('Run free5gc-ausf') {
 //              steps {
 //                 echo "command"
//
 //              }
 //           }
 //           stage('Run free5gc-nssf') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //           stage('Run free5gc-pcf') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //           stage('Run free5gc-nrf') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //           stage('Run free5gc-udm') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //           stage('Run free5gc-udr') {
 //              steps {
 //                 echo "command"
 //              }
 //           }
 //        }
 //        }

            stage('Docker Build for "smf" and "udm"') {
                     steps {
                           sh(script: """
                              cd free5gc-compose-master/nf_smf/
                  
                              docker images -a
                              docker build -t gradproj/nf-smf . 
                             
                              cd ..
                              cd /nf_udm/
                              docker scan
                              docker build -t gradproj/nf_udm . 
                              docker images -a                  
                        """)
                     }
                  }


                  stage('Login') {
                        steps {
                           sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        }
                     
                  }
                  stage('Push images in Docker-Hube') {
                        steps {

                        
                           sh(script: """

                              docker push gradproj/nf_smf:latest
                              docker push gradproj/nf_udm:latest

                              """ 
                           )
                           }

                  }   

                   stage('Logout') {
                     steps {
                         sh 'docker logout'
                             }
           
                   }  




                  
    }
    }


  





 