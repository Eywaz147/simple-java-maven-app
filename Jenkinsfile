pipeline {
    agent any

    tools {
        maven 'Maven 3'  // Ensure Maven is installed in Jenkins
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Eywaz147/simple-java-maven-app.git'  // Replace with your repo URL
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment commands here (e.g., SCP, Kubernetes, etc.)
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
