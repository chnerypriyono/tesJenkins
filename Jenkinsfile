pipeline {
	agent any
    stages {
        stage('build') {
            steps {
            	SLACK_POST_URL = credentials('WH_SLACK_ANDROID_DEV_BRANCH_BUILDER_INFO')
                sh "echo $SLACK_POST_URL"
            }
        }
    }
}