pipeline{
    environment {
    customImage = ''
  }
    
    agent any
    stages {
    stage('Git')
    {
    checkout scm
    }
    
    stage('Build')
    {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {

        def customImage = docker.build("simeensheikh/demoimage2")
    }

        stage ('PushImage')
        {
        /* Push the container to the custom Registry */
        customImage.push()
        }
    }
}

