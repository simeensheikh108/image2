pipeline{
    environment {
    def customImage = ''
  }
    
    agent any
    stages {
    stage('Git')
    {
	    steps {
    checkout scm
	    }
    }
    
    stage('Build')
    {
	    steps {
		    script {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {

        customImage = docker.build("simeensheikh/demoimage3")
    }
    }
    }
	}

        stage ('PushImage')
		{
	    steps {
		    script {
			  
		 docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {    
        /* Push the container to the custom Registry */
        customImage.push()
			}
		    }
			}
			}
    }
}
