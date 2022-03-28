#!groovy

testParams = [:]


pipeline {
  agent none  
  parameters {
    booleanParam(name: 'RELEASE_PACKAGE',
                 defaultValue: true,
                 description: 'THIS IS RELEASE PACKAGE')
    booleanParam(name: 'STAGE1',
                 defaultValue: true,
		 description: 'Run the STAGE1')	 
    choice(name: 'OR_PODS', choices: ['testbed1', 'testbed2', 'testbed3', 'testbed4'], description: 'This will work only stage1 is clicked')                 
    booleanParam(name: 'RUN_STAGE2',
                 defaultValue: false,
                 description: 'RUN_STAGE2')
    booleanParam(name: 'RUN_STAGE3',
                 defaultValue: false,
                 description: 'Run STAGE3')
  }


stages {
        stage('stage1') {
          when {
            expression { params.STAGE1 == true }
          }
          steps {
            script {
              var = params.OR_PODS
              echo "VAR  $var"               
            }
          }
        }
        stage('stage2') {
          when {
            expression { params.RUN_STAGE2 == true }
          }
          steps {
            script {
              echo "$params.RUN_STAGE2"               
            }
          }
        }
        stage('stage3') {
          when {
            expression { params.RUN_STAGE3 == true }
          }
          steps {
            script {
              echo "$params.RUN_STAGE3"                
            }
          }
        }        
      }
}
