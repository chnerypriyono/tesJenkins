pipeline {
	agent any
	environment {
		WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
	}
    stages {
        stage('build') {
            steps {
                script {
                    ERROR_LOG_FILENAME = UUID.randomUUID().toString()            
                }
                sh "echo $ERROR_LOG_FILENAME"
                sh "echo isi_file_error_log > ${ERROR_LOG_FILENAME}"
                script {
                    ERROR_LOG = readFile("${ERROR_LOG_FILENAME}").trim()
                }
                sh "rm ${ERROR_LOG_FILENAME}"
            }
        }
    }
    post {
     always {
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) has successfully built!:tada: Hurry up get the apk before it is gone!'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) build failed :cry: here is the preview message of what went wrong:\n\`\`\`${ERROR_LOG}\`\`\`'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
     }
    }
}