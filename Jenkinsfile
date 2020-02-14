pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
	stage('GetNodeName') {
		def node_name = "${NODE_NAME}"
		echo "The Node Name is: ${node_name}"
	}
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
