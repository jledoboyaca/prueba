node {
    agent {
        docker { image 'maven:3.9.3-eclipse-temurin-17' }
    }
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
        checkout scm
    }
    stage('Build') {
        sh "gradlew --version"
    }

    stage('Publish') {
        docker.withRegistry('http://10.50.6.29:9001', '6fa8ff4b-2f5c-43f2-b070-d87e840ebe31') {
    
            def customImage = docker.build("10.50.6.29:9001/ubuntu")

            /* Push the container to the custom Registry */
            customImage.push()
        }
    
    }
}
