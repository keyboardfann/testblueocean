pipeline {
    agent none
    stages {
        stage('Test') {
            agent { docker 'busybox' }
            steps {
                echo 'Testing..'
            }
        }

    }
    post {
	    success {
            slackSend color: '#7CFC00',
            message: "@channel ${env.JOB_BASE_NAME} success. (${env.BUILD_URL})"
        }
        failure {
            slackSend color: '#FF0000',
            message: "@channel ${env.JOB_BASE_NAME} failure. (${env.BUILD_URL})"
        }
        fixed {
            slackSend color: '#00FF00',
            message: "@channel ${env.JOB_BASE_NAME} back to success."
        }
    }
}
