pipeline {
    agent any
    
    environment {
        CI = 'true' // Setting the CI environment variable
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                git url: 'https://github.com/ni3pandharpatte/pw-del-me-repo.git', branch: 'main'
            }
        }
        stage('Setup Node.js') {
            steps {
                // Use the NodeJS plugin to set up Node.js
                // This assumes the NodeJS plugin is installed and configured
                nodejs(nodeJSInstallationName: 'NodeJS') {
                    // Print Node.js version
                    sh 'node --version'
                    // Print npm version
                    sh 'npm --version'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm ci'
            }
        }
        stage('Run Playwright Tests') {
            steps {
                // Install the Playwright browsers
                sh 'npx playwright install'
                // Run the Playwright tests
                sh 'npx playwright test'
            }
        }
    }
    
    post {
        always {
            // Archive test results or perform any cleanup here
            archiveArtifacts artifacts: 'test-results/**', allowEmptyArchive: true
            junit 'test-results/**/*.xml' // Adjust this if you have junit reports
        }
    }
}
