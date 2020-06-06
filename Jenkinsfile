pipeline {

  agent { label 'eroms-kubepod' }

  stages {
    // Stage 1 - Checking out this GIT repo
    stage('Checkout Source') {  
      steps {
        git url:'https://github.com/eromsu/playjenkins.git', branch:'test-deploy-stage'
      }
    }
    // Stage 2 - Deploying our k8s resources to k8s cluster
    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "myjenkinsplugink8s") // Using the Jenkins pluging (kubernetesDeploy) 
          // with k8s manifest file and k8s cluster credential "mykubeconfig" used by Jenkins to connect to cluster
        }
      }
    }

  }

}
