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
    def deployment = openshift.selector("dc", "backend-nueda1512") 
    
   if(!deployment.exists()){ 
      openshift.newApp('backend-nueda1512', "--as-deployment-config").narrow('svc').expose() 
    } 
    
    timeout(2) { 
      openshift.selector("dc", "backend-nueda1512").related('pods').untilEach(1) { 
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
