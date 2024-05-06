pipeline {
  agent any
  
  environment {
    VERCEL_TOKEN = 'NgAG88mWC7dktlzHz1YsnOgI' // Your Vercel token
    PROJECT_NAME = 'sample-nodejs-project'
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
          sh 'npm install vercel' // Install Vercel CLI locally
          sh 'vercel login'
          sh "vercel --token ${VERCEL_TOKEN} --prod" // Deploy to Vercel using the stored token
          sh './node_modules/.bin/vercel --token $VERCEL_TOKEN --prod' // Deploy to Vercel using local installation
        }
      }
    }
  }
}
