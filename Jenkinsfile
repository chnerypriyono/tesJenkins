pipeline {
	agent any
	environment {
		SLACK_POST_URL = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
	}
    stages {
        stage('build') {
            steps {
                sh "echo $SLACK_POST_URL"
            }
        }
    }
}