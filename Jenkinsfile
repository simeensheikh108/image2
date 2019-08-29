node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {

        def customImage = docker.build("simeensheikh/demoimage2")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
