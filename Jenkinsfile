pipeline {
    agent any
    stages {
	stage('Building SQL files->PKS files->PKB files') {
	node {
		// Checkout
  checkout scm

  // install required bundles
  bat script:'sh bundle install'

  // build and run tests with coverage
  bat script:'sh bundle exec rake build spec'

  // Archive the built artifacts
  archive (includes: 'pkg/*.gem')

  // publish html
  // snippet generator doesn't include "target:"
  // https://issues.jenkins-ci.org/browse/JENKINS-29711.
  publishHTML (target: [
      allowMissing: false,
      alwaysLinkToLastBuild: false,
      keepAll: true,
      reportDir: 'coverage',
      reportFiles: 'index.html',
      reportName: "RCov Report"
    ])
		notifyStarted()
	         //bat label: '', script: 'echo "Hello world"';
		      //bat script: 'echo Hello Ishita';
		      //bat script: 'cd C:/Users/itiwari/Documents/';
		      //bat script: 'echo $pwd';
		      //bat script: 'dir';
		      bat script: 'sh C:/Users/itiwari/Documents/All_In_One.sh';
		notifySuccessful()
		}
	}   
       
    }

}
def notifyStarted() {
  // send to Slack
  slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

  // send to HipChat
  hipchatSend (color: 'YELLOW', notify: true,
      message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
    )

  // send to email
  emailext (
      subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """
STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':


        
Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"

""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}



def notifySuccessful() {
  slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

  hipchatSend (color: 'GREEN', notify: true,
      message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
    )

  emailext (
      subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """
SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':


        
Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"

""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}



def notifyFailed() {
  slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")

  hipchatSend (color: 'RED', notify: true,
      message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
    )

  emailext (
      subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """
FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':


        
Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"

""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
} 
