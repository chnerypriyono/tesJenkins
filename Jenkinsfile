pipeline {
	agent any
	environment {
		WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
        i="a"
	}
    stages {
        stage('build') {
            steps {
                script {
                    String randomString = org.apache.commons.lang.RandomStringUtils.random(9, true, true)
                }
                sh "echo isi_file_error_log > error_log.txt"
                script {

                    ERROR_LOG = readFile('error_log.txt').trim()
                }
            }
        }
    }
    post {
     always {
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) has successfully built!:tada: Hurry up get the apk before it is gone!'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
        sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) build failed :cry: here is the preview message of what went wrong:${ERROR_LOG}'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
     }
    }
}