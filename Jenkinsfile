pipeline{
    environment {
    customImage = ''
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

        def customImage = docker.build("simeensheikh/demoimage2")
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
