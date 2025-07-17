 pipeline {
  agent any

 environment {
   SONAR_USER = "chandra"
   SONAR_PASS = "admin"
 }
   stages {
     stage('stage1 testing variables') {
       steps {
         script {
             // declaring the variable
             def abc = "hello"
             def xyz = "world"
             // 1st method of calling the variable
             print abc
             print xyz

             // 2nd method of calling the variable

             print "abc = ${abc}"
             print "xyz = ${xyz}"
          }
       }
    }
    stage('Quality Control') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'SONAR_AUTH', usernameVariable: 'SONAR_USER', passwordVariable: 'SONAR_PASS')]) {
      sh  "sonar-scanner -Dsonar.host.url=http://172.31.13.126:9000 -Dsonar.login=${SONAR_USER} -Dsonar.password=${SONAR_PASS} -Dsonar.projectKey=cart"
      }
    }
  }

}

