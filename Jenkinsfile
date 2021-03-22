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
        sshagent (['ubuntu']) {
       sh 'scp -o strictHostKeyChecking=no target/*.war ubuntu@18.188.24.16:/var/lib/tomcat9/webapps/webapp.war'
           
            }
         }
     }
  } 
}
