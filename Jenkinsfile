pipeline {
agent any
  tools {
  maven 'Maven'
        }
  
  stages {
    stage ('initialize') {
      steps {
             sh '''
              echo "PATH = $(PATH)"
              echo "M2_HOME = $(M2_HOME)"
              '''
             }
      }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
         }
       }
   stage ('Deploy-to-tomcat') {
      steps {
  sshagent(['tomcat9']) 
      sh 'scp  webapp/target/webapp.war ubuntu@3.141.98.170:/var/lib/tomcat9/webapps'     
            }
         }
     }
  } 
}
