pipeline {

  agent any
  
  stages {
  
    stage("prepare") {
     
      steps {
        echo '${pub_key}'
        echo '${BUILD_NUMBER}'
      }
    }
      
    stage("ansible") {
     
      steps {
        withCredentials([usernamePassword(credentialsId: "9942d12b-db6f-436e-aedb-17eeba1af897" , passwordVariable: 'my_Password', usernameVariable: 'my_User')]) {
          sh "sudo ansible-playbook -e \"my_user=${my_User} my_password=${my_Password}\" setup.yml"
        }
      }
    }
    
    stage("script") {
     
      steps {
        sh """
        chmod +x whats_going_on
        /usr/local/bin/python3 whats_going_on ${BUILD_NUMBER}
        """
      }
    }
  }
}
