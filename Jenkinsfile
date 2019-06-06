pipeline {

    agent any
 
    stages {
	    
	stage('Building SQL files') {
	steps {
		    dir("C:/Users/itiwari/Documents/SQL_Bucket")
		    {
		      sh SQL.sh
		    }
		}
	}   

	stage('Building PKS files') {
            steps {
            dir("C:/Users/itiwari/Documents")
		 {
                	sh PKS.sh
                }
            }
 
       }
  

	  stage('Building PKB files') {
            steps {
                dir("C:/Users/itiwari/Documentst")
                {
                	sh PKB.sh
                }
            }
 
        } 
    }

}
