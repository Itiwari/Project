pipeline {

    agent any
 
    stages {
        
	stage('Stage 1') {
	steps {
    dir("C:/Users/itiwari/Documents/SQL_Bucket")
    {
      sh ''' #!/bin/bash
		    for file in *; do
       		p="$(basename "$file")";
       		$(printf "@$p"|sqlplus system/Rajneeti007@$sid>>SQLLOG)  
	    	done
	    	echo "Successfully built .sql files!"
		'''
    }
		}
	}   

	stage('Stage 2') {
            steps {
            dir("C:/Users/itiwari/Documents/PKS_Bucket")
		            {
                sh ''' #!/bin/bash
		            for file in *; do
			        q="$(basename "$file")";
  			        $(printf "@$q"|sqlplus system/Rajneeti007@$sid>>SQLLOG)  
 			        done
		            echo "Successfully built .pks files!" 
         ''' 
                }
            }
 
       }
  

	  stage('Stage 3') {
            steps {
                dir("C:/Users/itiwari/Documents/PKB_Bucket")
                {
                sh '''#!/bin/bash
		        for file in *; do
			    r="$(basename "$file")";
  			    $(printf "@$r"|sqlplus system/Rajneeti007@$sid>>SQLLOG)  
			    done
		        echo "Successfully built .pkb files!"
                
         '''
                }
            }
 
        	} 
    }

}
