
pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
	agent any
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning..'
                 git 'https://github.com/Sonal0409/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
		  when{
			  branch 'Dev'
		  }
              steps{
                  echo 'complie the code..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		    when{
			  branch 'Dev'
		  }
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		     when{
			  branch 'test'
		  }
		  
              steps{
	         
                  sh 'mvn test'
              }
          
          }
           stage('MetricCheck'){
		   
		     when{
			  branch 'test'
		  }
              
              steps{
                  sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
              }
              
          	
          }
          stage('Package'){
		  
		    when{
			  branch 'Deploy'
		  }
		  
              steps{
		  
                  sh 'mvn package'
              }
          }
	     
	                stage('Deploy'){
		  
		    when{
			  branch 'Deploy'
		  }
		  
              steps{
		  
                  sh 'echo "deploy code"'
              }
          }
          
      }
}
