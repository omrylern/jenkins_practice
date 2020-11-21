pipeline {

  agent any
  
  stages {
  
    stage("Prepare") {
     
      steps {
        sh """
        echo ${pub_key} > public_key.pub
        ssh-keygen -l -f public_key.pub
        """
      }
    }
      
    stage("Ansible") {
     
      steps {
        withCredentials([usernamePassword(credentialsId: "9942d12b-db6f-436e-aedb-17eeba1af897" , passwordVariable: 'my_Password', usernameVariable: 'my_User')]) {
          sh "sudo ansible-playbook -e \"my_user=${my_User} my_password=${my_Password}\" setup.yml"
        }
      }
    }
    
    stage("Script") {
     
      steps {
        sh """
        chmod +x whats_going_on
        /usr/local/bin/python3 whats_going_on ${BUILD_NUMBER}
        """
        archiveArtifacts artifacts: 'data.json', onlyIfSuccessful: true
      }
    }
  }
  post {
    failure {
      echo "The string entered is not a valid RSA key. Please check it again and try the build again."
}
