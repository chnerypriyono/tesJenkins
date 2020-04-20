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
                    FOO = "test2"
                }
                sh "echo ${FOO}"
                script {
                    FOO = "test3"
                }
                sh "echo ${FOO}"
                sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) has successfully built!:tada: Hurry up get the apk before it is gone!'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
                sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$JOB_NAME ($BUILD_URL) build failed :cry: here is the preview message of what went wrong:${FOO}'}\" $WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO"
            }
        }
    }
}