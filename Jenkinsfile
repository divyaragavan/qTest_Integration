#!groovy

testParams = [:]

def runTest(application) {  
      try {
        echo "application: $application"        
        sh "make test-leaf-spine-onboarding"
      }catch(Exception e) {
        echo  "ERROR"
       }
}

pipeline {
  agent none  
  parameters {
    booleanParam(name: 'leaf_spine_onboarding',
                 defaultValue: true,
		 description: 'Run the leaf_spine_onboarding test suite')	 
    choice(name: 'OR_PODS', choices: ['testbed1', 'testbed2', 'testbed3', 'testbed4'], description: 'This will work only stage1 is clicked')                 
  }

stages {
        stage('stage1') {
          when {
            expression { params.leaf_spine_onboarding == true }
          }
          steps {
            script {
              var = params.OR_PODS
              echo "VAR  $var"	      
               runTest('leaf-spine-onboarding')
            }
          }
        }     
      }
}
