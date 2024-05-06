pipeline {
    agent any
    
    environment {
        VERCEL_TOKEN = 'NgAG88mWC7dktlzHz1YsnOgI' // Your Vercel token
        PROJECT_NAME = 'sample-nodejs-project' // Name of your Vercel project
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
        
        stage('Deploy to Vercel') {
            steps {
                script {
                    // Install Vercel CLI locally
                    sh 'npm install vercel'
                    
                    // Deploy to Vercel using local installation
                    sh "./node_modules/.bin/vercel --token $VERCEL_TOKEN --prod --confirm --project $PROJECT_NAME"
                }
            }
        }
    }
}
