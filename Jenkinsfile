pipeline {
    agent any
    
    environment {
        DOTNET_CLI_HOME = "${WORKSPACE}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out from Git'
            }
        }
        
        stage('Restore') {
            steps {
                echo 'Restoring NuGet packages...'
                bat 'dotnet restore'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building project...'
                bat 'dotnet build --configuration Release'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'dotnet test --no-build'
            }
        }
        
        stage('Publish') {
            steps {
                echo 'Publishing application...'
                bat 'dotnet publish --configuration Release --output ./publish'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'echo Deployment complete! Files are in ./publish folder'
                bat 'dir ./publish'
            }
        }
    }
    
    post {
        success {
            echo '✅ Build and Deploy succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
        always {
            echo 'Cleaning up...'
        }
    }
}
