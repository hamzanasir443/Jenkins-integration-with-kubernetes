pipeline {

  environment {
    ARTIFACTORY_CREDENTIALS=credentials('2e8b5912-b6a0-4704-bf87-e5db31752bfd')
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/hamzanasir443/Jenkins-integration-with-kubernetes.git'
      }
    }
    stage('Login') {

	   steps {
		 sh 'echo $ARTIFACTORY_CREDENTIALS_PSW | docker login erl-artifactory7.eso.local -u $ARTIFACTORY_CREDENTIALS_USR --password-stdin'
		 	}
		 } 
    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
