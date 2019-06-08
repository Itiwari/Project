pipeline {
    agent any
    environment {
        //This variable need be tested as string
        doError = '0'
       
    }
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
        
        stage('Success') {
            when {
                expression { doError == '0' }
            }
            steps {
                echo "ok"
            }
        }
    }  //stages over
    post {
        always {
            echo 'I will always say Hello again!'
            
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
        }
  

