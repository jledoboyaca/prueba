node {
    def mvnHome
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
        checkout scm
    }
    stage('Build') {
        docker.build("10.50.6.29:9001/ubuntu")
    }
    stage('Build-gradle') {
            agent {
                docker {
                    image 'gradle:8.2.0-jdk17-alpine'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
                }
            }
            steps {
                sh 'gradle --version'
            }
    }
    
    stage('Publish') {
        docker.withRegistry('http://10.50.6.29:9001', '6fa8ff4b-2f5c-43f2-b070-d87e840ebe31	') {
    
            def customImage = docker.build("10.50.6.29:9001/ubuntu")
    
            /* Push the container to the custom Registry */
            customImage.push()
        }
    
    }
}
