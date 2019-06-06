pipeline {

    agent any
 
    stages {
	    stage('Putting files in separate buckets'){
		    steps{
			 dir("C:/Program Files (x86)/Jenkins/workspace/Tuesday_Test4")
			    {
				sh ''' #!/bin/bash
				for file in *;
				 do
				      if [ ${file:(-3)} == "sql" ];
				       then
					a="$(basename "$file")";
					cat $a > C:/Users/itiwari/Documents/SQL_Bucket/$a
				      elif [ ${file:(-3)} == "pks" ];
				       then
					b="$(basename "$file")";
					cat $b > C:/Users/itiwari/Documents/PKS_Bucket/$b
					elif [ ${file:(-3)} == "pkb" ];
				       then
					c="$(basename "$file")";
					cat $c > C:/Users/itiwari/Documents/PKB_Bucket/$c
				      fi
				 done
				 '''
			   }
		    }
	    }  
	stage('Building SQL files') {
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

	stage('Building PKS files') {
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
  

	  stage('Building PKB files') {
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
