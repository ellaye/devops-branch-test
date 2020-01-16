pipeline{
    agent {
        node {
            label 'base'
        }
    }

    environment{
        KUBECONFIG_CREDENTIAL_ID = 'demo-kubeconfig'
    }

    stages {
	   stage ('checkout scm') {
               steps {
		 echo '1'
                 checkout(scm)
               }
            }
		
	   stage('deploy'){
               steps{
                 kubernetesDeploy(configs: 'deploy/devops-nginx/**', deleteResource: true, enableConfigSubstitution : true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
                 sh 'echo master'
                 }
	    }
     }
}
