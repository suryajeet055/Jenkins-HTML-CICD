
pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:/JenkinsDeploy'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading project from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/Jenkins-HTML-CICD.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Checking project files...'
                bat 'dir'
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist style.css exit /b 1'
                bat 'if not exist script.js exit /b 1'
                echo 'All required files are available.'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing HTML and JavaScript file availability...'
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist script.js exit /b 1'
                echo 'Basic file tests passed.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'
                bat 'if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"'
                bat 'copy /Y index.html "%DEPLOY_DIR%\\index.html"'
                bat 'copy /Y style.css "%DEPLOY_DIR%\\style.css"'
                bat 'copy /Y script.js "%DEPLOY_DIR%\\script.js"'
                echo 'Website files deployed successfully.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the Console Output.'
        }
    }
}
