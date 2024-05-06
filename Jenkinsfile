pipeline {
    agent any
    
    environment {
        VERCEL_TOKEN = 'NgAG88mWC7dktlzHz1YsnOgI' // Your Vercel token
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
                    sh './node_modules/.bin/vercel --token $VERCEL_TOKEN --prod' // Deploy to Vercel using local installation
                }
            }
        }
        
        stage("Zip Repository") {
            steps {
                // Create a zip archive of the entire repository
                sh 'zip -r repository.zip .'
            }
        }
        
        stage("Publish to S3") {
            steps {
                // Upload the zip archive to S3
                s3Upload(
                    bucket: 'sanket-artifact-store',
                    consoleLogLevel: 'INFO',
                    dontSetBuildResultOnFailure: false,
                    dontWaitForConcurrentBuildCompletion: false,
                    entries: [[sourceFile: 'repository.zip']],
                    pluginFailureResultConstraint: 'FAILURE',
                    selectedRegion: 'us-east-1',
                    showDirectlyInBrowser: false,
                    uploadFromSlave: false
                )
            }
        }
    }
}
