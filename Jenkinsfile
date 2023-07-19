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
        docker.push("10.50.6.29:9001/ubuntu")
    
    }
}
