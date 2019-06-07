pipeline {
    agent any
    stages {
	stage('Building SQL files->PKS files->PKB files') {
	steps {
	         //bat label: '', script: 'echo "Hello world"';
		      //bat script: 'echo Hello Ishita';
		      //bat script: 'cd C:/Users/itiwari/Documents/';
		      //bat script: 'echo $pwd';
		      //bat script: 'dir';
		      bat script: 'sh C:/Users/itiwari/Documents/All_In_One.sh';
		}
	}   
       
    }

}
post {
        always {
            echo 'This will always run'
	mail bcc: '', body: "<b>Example</b><br>\n\<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "tiwariishita090@gmail.com";
       	
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
	//mail bcc: '', body: "<b>Example</b><br>\n\<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "tiwariishita090@gmail.com";
       
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
