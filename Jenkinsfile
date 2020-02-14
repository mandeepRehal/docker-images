pipeline {
  agent 'windows-pod-9hqvx-70v1x'
  options { 
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test-windows') {
      agent {
        kubernetes {
	  label 'windows-pod'
          yamlFile 'windows/dotnet-pod.yaml'
        }
      }
      steps {
        bat 'dir'
        container(name:'windows-dotnet'){
          bat 'dotnet -h'
      } 
     }
    }
  }
}
