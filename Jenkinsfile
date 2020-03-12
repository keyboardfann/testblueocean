def label = "slave-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [																				   
  containerTemplate(name: 'test', image: 'busybox', alwaysPullImage: true)
																						
],
volumes: [
																			
  hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
]) {
  node(label) {
    def myRepo = checkout scm
    def gitCommit = myRepo.GIT_COMMIT
    def gitBranch = myRepo.GIT_BRANCH
 
    stage('Test') {
      try {
        container('test') {
          sh """
            pwd
            echo "GIT_BRANCH=${gitBranch}" >> /etc/environment
            echo "GIT_COMMIT=${gitCommit}" >> /etc/environment
            echo "Testing 123456"
            """
        }
      }
      catch (exc) {
        println "Failed to test - ${currentBuild.fullDisplayName}"
        throw(exc)
										 
      }
    }
							 
							
										   
							 
	   
	 
						  
						 
										 
					  
	   
	 
  }
}
