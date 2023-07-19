node {
    def mvnHome
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
        checkout scm
    }
    stage('Build') {
        docker.build("10.50.6.29:9001/ubuntu")
    }
    stage('Publish') {
        docker.withRegistry('http://10.50.6.29:9001', 'jLedo') {
    
            def customImage = docker.build("10.50.6.29:9001/ubuntu")
    
            /* Push the container to the custom Registry */
            customImage.push()
        }
    
    }
}
