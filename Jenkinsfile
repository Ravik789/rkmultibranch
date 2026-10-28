
pipeline {
    agent any

    stages {
        stage('Show Branch') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Python') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Run Application') {
            steps {
                sh 'python3 app.py'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m unittest discover -v'
            }
        }

        stage('Deploy to DEV') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Demo: Deploying to DEV environment'
            }
        }

        stage('Deploy to PROD') {
            when {
                branch 'main'
            }
            steps {
                echo 'Demo: Deploying to PROD environment'
            }
        }
    }

    post {
        success {
            echo 'Build and tests passed!'
        }
        failure {
            echo 'Build failed. Check Console Output.'
        }
    }
}
