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
                sh 'echo "isi_file_error_log\nWhat went wrong:\nbaris bawahnya" >' + "${ERROR_LOG_FILENAME}"
                script {
                    ERROR_LOG = '_' + sh (script: "grep \"What went wrong\" ${ERROR_LOG_FILENAME} -B 10 -A5", returnStdout: true).trim() + '_'
                    //ERROR_LOG = '_' + readFile("${ERROR_LOG_FILENAME}").trim() + '_'
                    sh "rm ${ERROR_LOG_FILENAME}"
                }
            }
        }
    }
    post {
     always {
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) has successfully built!:tada: Hurry up get the apk before it is gone!'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) build failed :cry: here is the preview message of what went wrong:\n${ERROR_LOG}'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
     }
    }
}