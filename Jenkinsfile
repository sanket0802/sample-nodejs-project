pipeline {
  agent any
  
  environment {
    VERCEL_TOKEN = 'vsbQTs02wPrFsJtwMXRRNSI9' // Your Vercel token
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
    
    stage('Install Vercel CLI') {
      steps {
        script {
          sh 'npm install -g vercel'
        }
      }
    }
    
    stage('Deploy to Vercel') {
      steps {
        script {
          sh './node_modules/.bin/vercel --token $VERCEL_TOKEN --prod' // Deploy to Vercel using local installation
        }
      }
    }
  }
}
