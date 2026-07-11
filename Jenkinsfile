pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install') {
            steps {
                bat 'echo Running tests...'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Installing dependencies...'
            }
        }

        stage('Build') {
            steps {
                bat
                if exist dist rmdir /S /Q dist
                mkdir dist
                xcopy index.html dist\\ /Y
                xcopy css dist\\css\\ /E /Y
                xcopy js dist\\js\\ /E /Y
            }
        }

        stage('Deploy Dev') {
            steps {
                bat 'xcopy dist C:\\deployments\\development\\ /E /Y'
            }
        }

        stage('Deploy Staging') {
            steps {
                bat 'xcopy dist C:\\deployments\\staging\\ /E /Y'
            }
        }

        stage('Deploy Production') {
            when {
                branch 'main'
            }
            steps {
                bat 'xcopy dist C:\\deployments\\production\\ /E /Y'
            }
        }
    }
}