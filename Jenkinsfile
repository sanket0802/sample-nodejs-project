pipeline {
    agent any
    
    environment {
        VERCEL_TOKEN = 'NgAG88mWC7dktlzHz1YsnOgI' // Your Vercel token
        PROJECT_NAME = 'test-project' // Name of your Vercel project
    }
    
    stages {
        stage('Build') {
            steps {
                nodejs('Node') {
                    echo 'Building Application.....'
                    sh 'npm install'
                }
            }
        }
        
        stage('Select Vercel Project') {
            steps {
                script {
                    // Install Vercel CLI locally
                    sh 'npm install -g vercel'
                    
                    // Switch to the specified project
                    sh "vercel switch $PROJECT_NAME --token $VERCEL_TOKEN"
                }
            }
        }
        
        stage('Deploy to Vercel') {
            steps {
                script {
                    // Deploy to Vercel using local installation
                    sh 'vercel --prod'
                }
            }
        }
    }
}
