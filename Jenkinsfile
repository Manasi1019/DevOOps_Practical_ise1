pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the project..."
                // Add your build commands here
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                // Add your test commands here
            }
        }
    }

    post {
        success {
            emailext(
                subject: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Good news! The build succeeded.\n\nCheck details: ${env.BUILD_URL}",
                to: "manasipatil102021@gmail.com"
            )
        }
        failure {
            emailext(
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Oops! The build failed.\n\nCheck details: ${env.BUILD_URL}",
                to: "manasipatil102021@gmail.com"
            )
        }
        always {
            emailext(
                subject: "Build Finished: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build finished. Status: ${currentBuild.currentResult}\n\nDetails: ${env.BUILD_URL}",
                to: "manasipatil102021@gmail.com"
            )
        }
    }
}
