pipeline {

  agent any
  
  stages {
  
    stage("prepare") {
     
      steps {
        echo 'Prepare for take off...'
      }
    }
      
    stage("ansible") {
     
      steps {
        echo 'creating user bob...'
      }
    }
    
    stage("script") {
     
      steps {
        sh """
        chmod +x whats_going_on
        python3 whats_going_on
        """
      }
    }
  }
}
