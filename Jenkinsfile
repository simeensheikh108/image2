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

        customImage = docker.build("simeensheikh/demoimage4")
    }
    }
    }
	}
	    
    stage('Aqua')
	    {
		    steps
		    {
			    script {
				     aquaMicroscanner imageName: 'simeensheikh/demoimage4', notCompliesCmd: 'exit 1', onDisallowed: 'fail', outputFormat: 'html'
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
