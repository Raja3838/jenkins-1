pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Define the folder where you want to clone the Git repository
                script {
                    def gitFolder = '/home/ec2-user/test'
                    
                    // Clean up the workspace before cloning
                    deleteDir()
                    
                    // Clone the Git repository into the specified folder
                    checkout scm: [$class: 'GitSCM', branches: [[name: '*/develop']], userRemoteConfigs: [[url: 'https://github.com/Raja3838/jenkins-1.git']]], poll: false, workspaceUpdater: [$class: 'UpdateUpdater']
                }
            }
        }
        
        stage('Build') {
            steps {
                // Add your build steps here if needed
                // For example, you can run build scripts, compile code, etc.
                sh 'echo "Building..."'
            }
        }
        
        // Add more stages for additional actions or deployment steps as needed
    }
    
    post {
        success {
            // This block will be executed if the pipeline succeeds
            echo 'Pipeline succeeded!'
        }
        
        failure {
            // This block will be executed if the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
