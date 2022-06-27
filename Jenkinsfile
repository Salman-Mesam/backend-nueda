def projectName = '8dfoodh-dev'
def version = "0.0.${currentBuild.number}"
def dockerImageTag = "${projectName}:${version}"

pipeline {
  agent any

  stages {

    stage('Build Container') {
      steps {
        dir("springboot-backend"){
           sh "docker build -t ${dockerImageTag} ."
        }
       
      }
    }

    stage('Deploy Container To Openshift') {
      steps {
        sh "oc login --token=sha256~QNF-cZ7rtSzpcuRWcLaxVmuV6txVpfVQAaESEnt8Lpw --server=https://api.sandbox-m2.ll9k.p1.openshiftapps.com:6443"
        sh "oc project ${projectName} || oc new-project ${projectName}"
        sh "oc delete all --selector app=${projectName} || echo 'Unable to delete all previous openshift resources'"
        sh "oc new-app ${dockerImageTag} -l version=${version}"
        sh "oc expose dc ${projectName} --port=8090"
        sh "oc expose svc ${projectName}"
      }
    }
  }
}
