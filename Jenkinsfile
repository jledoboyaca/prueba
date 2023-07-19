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
        docker.withRegistry('http://10.50.6.29:9001', '6fa8ff4b-2f5c-43f2-b070-d87e840ebe31	') {
    
            def customImage = docker.build("10.50.6.29:9001/ubuntu")

            customImage.inside {
                sh 'echo test'
            }
            
            /* Push the container to the custom Registry */
            customImage.push()
        }
    
    }
}
