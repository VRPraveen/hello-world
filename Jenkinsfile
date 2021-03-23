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
    sshagent(['3.141.98.170']) {
    // some block
}
    stage ('Deploy-to-tomcat') {
      steps {
     sshagent (['ubuntu']) {
        sh 'scp  webapp/target/webapp.war ubuntu@3.141.98.170:/var/lib/tomcat9/webapps'
           
            }
         }
     }
  } 
}
