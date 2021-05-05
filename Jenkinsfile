node {

	checkout scm
	
	environment {
	    dockerImage = ''
	}
	
    docker.withRegistry('https://registry.hub.docker.com', 'dockerHubCredentials') {
	    def img = docker.build("nirushanth/student-demo")
	    img.push()
    }
    
  stage('Apply Kubernetes files') {
    withKubeConfig([credentialsId: 'kubeconfig1']) {
		sh 'kubectl apply -f kubernetes/student-demo-deployment.yml'
    }
  }
}