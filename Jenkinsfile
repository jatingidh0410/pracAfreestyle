pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Pulls the index.html from your main branch
                checkout scm
            }
        }

        stage('Deploy HTML') {
            steps {
                echo 'Deploying HTML file to local directory...'
                // Using 'bat' because Jenkins is running on Windows
                bat 'if not exist C:\\JenkinsTestDeployPipeline mkdir C:\\JenkinsTestDeployPipeline'
                bat 'copy index.html C:\\JenkinsTestDeployPipeline\\'
            }
        }
    }

    post {
        always {
            // This replaces the "Archive the artifacts" post-build action
            archiveArtifacts artifacts: 'index.html', fingerprint: true
        }
        success {
            echo 'Pipeline successfully completed!'
        }
    }
}
