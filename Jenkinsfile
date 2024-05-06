pipeline {
  agent any
  
  environment {
    VERCEL_TOKEN = 'vsbQTs02wPrFsJtwMXRRNSI9' // Using the credential ID 'vercel-token'
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
          withCredentials([string(credentialsId: 'vercel-token', variable: 'VERCEL_TOKEN')]) {
            sh 'npm install -g vercel' // Install Vercel CLI globally
            sh 'vercel --token $VERCEL_TOKEN --prod' // Deploy to Vercel
          }
        }
      }
    }
  }
}
