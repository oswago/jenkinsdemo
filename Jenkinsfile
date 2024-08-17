pipeline {
    agent any

    stages {
        stage('One') {
            steps {
                echo 'Building for the Oswagos................'
            }
        }
        
        stage('Two') {
            steps {
                input('Do you want to proceed?')
            }
        }
        
        stage('Three') {
		    when{
			     not{
				 branch 'master'
				 }
			  }
            steps {
                echo 'Hello.......'

            }
        }
		
		stage('Four') {
                   parallel{
				      stage('Unit Test'){
					     steps{
						 echo 'Running the Unit Test......'
						 }
					  }
				     stage('Integration test'){
					      agent{
						       docker{
							     reuseNode false
								 image 'Ubuntu'
							   }
						  }
						  steps{
						     echo 'Running the Integration test........'
						  }
					 }
				   }
        }
