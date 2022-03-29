#!groovy

def runTest(application) {
		echo "application: $application"
		dir("test-${application}") {
			a = sh "pwd"
			sh "echo $a"
			sh "cd /home/developer/qtest/qTest_Integration/src && make test-leaf-spine-onboarding"
			sh "ls -lrt /root/.jenkins/workspace/divyaragavan_fork_main/src/test_results"
			//sh "make test-leaf-spine-onboarding"
		}
}

testParams = [:]

pipeline {
  agent any
  parameters {
    separator(name: "LEAF_SPINE_ONBOARDING_SECTION", sectionHeader: "Leaf spine onboarding stage can run with any OR-pods (s,m,l,xl) by choosing the option")
    booleanParam(name: 'leaf_spine_onboarding',
                 defaultValue: true,
		 description: 'Run the leaf_spine_onboarding test suite')	 
    choice(name: 'OR_PODS', choices: ['testbed1', 'testbed2', 'testbed3', 'testbed4'], description: 'This will work only stage1 is clicked')
    separator(name: "LAST_AUTOMATION")
    booleanParam(name: 'PublishRobotResults',
                 defaultValue: true,
		 description: 'publish robot results')	  
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
	stage('PublishRobotResults') {
              agent any
	    when {
                 expression { params.PublishRobotResults == true }
              }
              steps {
              robot archiveDirName: 'robot-plugin', logFileName: 'log.html', outputFileName: 'output.xml', outputPath: '/home/developer/qtest/qTest_Integration/src/test_results', overwriteXAxisLabel: '', reportFileName: 'report.html'
              }
            } 
        stage('Publish') {
              agent any
	      when {
                 expression { params.Publish == true }
              }             		
              steps {
		//junit(allowEmptyResults: true,testResults: '*.xml')
		//xunit testDataPublishers: [attachments()], tools: [JUnit(excludesPattern: '', failIfNotNew: false, pattern: '', skipNoTestFiles: true, stopProcessingIfError: true)]
                submitJUnitTestResultsToqTest([apiKey: 'cc212465-8fa4-4707-8955-5d0fb1da9ebe', containerID: 280309, containerType: 'release', createTestCaseForEachJUnitTestClass: true, createTestCaseForEachJUnitTestMethod: false, overwriteExistingTestSteps: true, parseTestResultsFromTestingTools: true, parseTestResultsPattern: '/root/.jenkins/workspace/divyaragavan_fork_main/src/test_results/*.xml', projectID: 73444, qtestURL: 'https://smartrg.qtestnet.com', submitToAReleaseAsSettingFromQtest: true, submitToExistingContainer: false, utilizeTestResultsFromCITool: false])
              }
              }        
      }
}
