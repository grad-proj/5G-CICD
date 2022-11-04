pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }




      stage('Ueransim') {
         parallel {
            stage('Run gnb') {
               steps {
                  echo "command"

               }
            }
            stage('Run ue') {
               steps {
                  echo "command"
               }
            }
         }
         }





      stage('Free5gc') {
         parallel {
            stage('Run free5gc-amf') {
               steps {
                  echo "command"

               }
            }
            stage('Run free5gc-smf') {
               steps {
                  echo "command"
               }
            }
         }
         }




      stage('Free5gc-2') {
         parallel {
            stage('Run free5gc-ausf') {
               steps {
                  echo "command"

               }
            }
            stage('Run free5gc-nssf') {
               steps {
                  echo "command"
               }
            }
            stage('Run free5gc-pcf') {
               steps {
                  echo "command"
               }
            }
            stage('Run free5gc-nrf') {
               steps {
                  echo "command"
               }
            }
            stage('Run free5gc-udm') {
               steps {
                  echo "command"
               }
            }
            stage('Run free5gc-udr') {
               steps {
                  echo "command"
               }
            }
         }
         }



      stage('Docker Build') {
         steps {
               sh(script: """
                  cd Dockerfile/
                 
                  cd nf_amf/
                   docker images -a
                   docker build -t gradproj/nf-amf . 
                   docker images -a 

                  cd ..
                  cd nf_n3iwf/
                   docker build -t gradproj/n3iwf . 
                   docker images -a                  
            """)
         }
      }
      stage ('Push Docker image'){

            steps{
                echo "============Pushing Docker image==========="
             withCredentials([usernamePassword(credentialsId: 'DockerHUB', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')])
                {
                sh """
                    docker login -u ${USERNAME} -p ${PASSWORD}
                    docker push gradproj/amf:latest
                    docker push gradproj/n3iwf:latest
                    """ 
                }
            }



    }
    }

    }


