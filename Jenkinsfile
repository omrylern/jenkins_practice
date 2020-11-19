pipeline {

  agent any
  
  stages {
  
    stage("prepare") {
     
      steps {
        echo 'Prepare for take off...'
        sh "ls -l"
      }
    }
      
    stage("ansible") {
     
      steps {
        withCredentials([usernamePassword(credentialsId: "9942d12b-db6f-436e-aedb-17eeba1af897" , passwordVariable: 'Password', usernameVariable: 'bob')]) {
       // sh "ansible-playbook setup.yml"
        }
      }
    }
    
    stage("script") {
     
      steps {
        sh """
        whoami
        echo $PATH
        chmod +x whats_going_on
        /usr/local/bin/python3 whats_going_on
        """
      }
    }
  }
}
