#!groovy

testParams = [:]

def runTest(application) {  	
        echo "application: $application" 
	//sh "robot -P /tmp/build -d test_results -L DEBUG -b debug.txt --extension rst test_suite/leaf-spine-onboarding"
}

pipeline {
  agent none  
  parameters {
    booleanParam(name: 'leaf_spine_onboarding',
                 defaultValue: true,
		 description: 'Run the leaf_spine_onboarding test suite')	 
    choice(name: 'OR_PODS', choices: ['testbed1', 'testbed2', 'testbed3', 'testbed4'], description: 'This will work only stage1 is clicked')                 
  }
  
  node("myAgent") {
  stages {
        stage('stage1') {
	  //agent { label 'Built-In Node' }
          when {
            expression { params.leaf_spine_onboarding == true }
          }
          steps {
            script {
              var = params.OR_PODS
              echo "VAR  $var"	
	      runTest("leaf-spine-onboarding")
            }
          }
        }     
      }
  }
}

