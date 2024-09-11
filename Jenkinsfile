pipeline {
    agent any
    
    environment {
        // Define any environment variables like the Java version or any credentials you need
        MAVEN_OPTS = "-Xms256m -Xmx512m"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git credentialsId: 'github-token', url: 'https://github.com/KoushalKumar22/Jenkins-pipeline-with-github.git'
            }
        }
        stage('Build') {
            steps {
                // Build the project using Maven
                echo 'Building the project...'
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                // Package the application (create a JAR file)
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}
