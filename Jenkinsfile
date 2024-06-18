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
               bat 'node --version'
               bat 'npm --version'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                bat 'npm ci'
            }
        }
        stage('Run Playwright Tests') {
            steps {
                // Install the Playwright browsers
                bat 'npx playwright install'
                // Run the Playwright tests
                bat 'npx playwright test'
           }
        }
    }
}
