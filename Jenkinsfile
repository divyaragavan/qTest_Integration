#!groovy

def runTest(application) {
		echo "application: $application"
	try{
		dir("test-${application}") {
			a = sh "pwd"
			sh "echo $a"
			sh "cd /home/developer/qtest/qTest_Integration/src && make test-leaf-spine-onboarding"
			//sh "make test-leaf-spine-onboarding"
		}
	}finally {
        archiveArtifacts artifacts: "**/test_results/**", allowEmptyArchive: false
        }
}

testParams = [:]

pipeline {
  agent any
  parameters {
    booleanParam(name: 'leaf_spine_onboarding',
                 defaultValue: true,
		 description: 'Run the leaf_spine_onboarding test suite')	 
    choice(name: 'OR_PODS', choices: ['testbed1', 'testbed2', 'testbed3', 'testbed4'], description: 'This will work only stage1 is clicked')  
    booleanParam(name: 'Publish',
                 defaultValue: true,
		 description: 'publish results to qtest')	     
  }


stages {		
        stage('Test Leaf Spine Onboarding') {
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
        stage('Publish') {
              agent any
              steps {
                submitJUnitTestResultsToqTest([apiKey: 'cc212465-8fa4-4707-8955-5d0fb1da9ebe', containerID: 280309, containerType: 'release', createTestCaseForEachJUnitTestClass: false, createTestCaseForEachJUnitTestMethod: true, overwriteExistingTestSteps: true, parseTestResultsFromTestingTools: true, projectID: 73444, qtestURL: 'https://smartrg.qtestnet.com/', submitToAReleaseAsSettingFromQtest: true, submitToExistingContainer: false, utilizeTestResultsFromCITool: false])
              }
              }        
      }
}
