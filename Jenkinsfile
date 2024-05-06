pipeline {
    agent any
    
    environment {
        VERCEL_TOKEN = 'NgAG88mWC7dktlzHz1YsnOgI' // Your Vercel token
        PROJECT_NAME = 'smaple-nodejs-project' // Name of your Vercel project
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
        
        stage('Login to Vercel') {
            steps {
                script {
                    // Install Vercel CLI locally
                    sh 'npm install vercel'
                    
                    // Authenticate with Vercel using the token
                    sh "vercel login --token $VERCEL_TOKEN"
                }
            }
        }
        
        stage('Select Vercel Project') {
            steps {
                script {
                    // Switch to the specified project
                    sh "vercel switch $PROJECT_NAME"
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
