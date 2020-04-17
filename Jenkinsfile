pipeline {
	agent any
	environment {
		SLACK_POST_URL = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
	}
    stages {
        stage('build') {
            steps {
                sh "curl -X POST -H 'Content-type: application/json' --data \"{'text':'$BUILD_URL has failed'}\" $SLACK_POST_URL"
            }
        }
    }
}