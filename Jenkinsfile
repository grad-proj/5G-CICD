pipeline {
   agent any


   
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

               stage('Login') {
                       steps{
                
             withCredentials([usernamePassword(credentialsId: 'DockerHUB', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])
                {
                sh """
                    docker login -u ${USERNAME} -p ${PASSWORD}
                  """
                }
               
            }
               }
            stage('Docker Build for "smf" and "udm"') {
                     steps {
                           sh(script: """
                              cd free5gc-compose-master/nf_udm/
                  
                              docker images -a
                              
                              docker build -t gradproj/nf_udm . 
                              docker images -a                  
                        """)
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


  





 