pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                echo '🔄 Cloning your GitHub repository...'
                git branch: 'main', url: 'https://github.com/vishnuvardhan439/personal_Blog-wedsite.git'
            }
        }

        stage('Build') {
            steps {
                echo '🏗️ Building the project (if needed)...'
                // Add build commands here if you later use frameworks like React or Hugo
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying website files to local web folder...'
                bat '''
                if not exist "C:\\xampp\\htdocs\\personal_blog" mkdir "C:\\xampp\\htdocs\\personal_blog"
                xcopy "%WORKSPACE%\\*" "C:\\xampp\\htdocs\\personal_blog" /E /Y
                '''
            }
        }

        stage('Preview') {
            steps {
                echo '🌐 Opening your site in browser...'
                bat 'start http://localhost/personal_blog'
            }
        }
    }

    post {
        success {
            echo '✅ Website deployed and preview opened successfully!'
        }
        failure {
            echo '❌ Deployment failed — check the console output for errors.'
        }
    }
}
