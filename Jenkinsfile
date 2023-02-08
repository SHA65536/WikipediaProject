pipeline {
    agent {
        docker {
            image 'golang:latest'
        }
    }

    stages {
        stage('Build') {
            steps {
                // Build the application
                sh "export GOCACHE=/tmp/.cache; go build ./cmd/linkapi"
            }
        }
        stage('Test') {
            steps {
                // Test the application
                sh "export GOCACHE=/tmp/.cache; go test ./..."
            }
        }
        stage('Push') {
            steps {
                // Push to S3
                sh "aws s3 cp ./linkapi s3://cloudschoolproject-buildartifacts/linkapi"
            }
        }
    }
}