pipeline {

  agent {
    label 'maven'
  }

  stages {
  
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        script {

          openshift.withCluster() { 
  openshift.withProject("8dfoodh-dev") { 
    def deployment = openshift.selector("dc", "backend-nueda") 
    
   
    
    timeout(5) { 
      openshift.selector("dc", "backend-nueda").related('pods').untilEach(1) { 
        return (it8dfoodh-devhase == "Running") 
      } 
    } 
  } 
}

        }
      }
    }
  }
}
