pipeline {
	agent any
	environment {
		WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
	}
    stages {
        stage('build') {
            steps {
            for (i in [ 'a', 'b', 'c' ]) {
                echo i
                sh 'echo "from shell i=$i"'
            }
                sh "ERROR_LOG=blablabla"
                sh 'echo "$ERROR_LOG"'
                sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) has successfully built!:tada: Hurry up get the apk before it is gone!'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
                sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) build failed :cry: here is the preview message of what went wrong:\\$ERROR_LOG'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
            }
        }
    }
}