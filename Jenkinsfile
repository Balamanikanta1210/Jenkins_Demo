pipeline {
	    agent any
	

	        // Environment Variables
	        environment {
	        MAJOR = '1'
	        MINOR = '0'
	        //Orchestrator Services
	        UIPATH_ORCH_URL = "https://cloud.uipath.com/"
	        UIPATH_ORCH_LOGICAL_NAME = "eld"
	        UIPATH_ORCH_TENANT_NAME = "DefaultTenant"
	        UIPATH_ORCH_FOLDER_NAME = "Test"
	    }
	

	    stages {
	

	        // Printing Basic Information
	        stage('Preparing'){
	            steps {
	                echo "Jenkins Home ${env.JENKINS_HOME}"
	                echo "Jenkins URL ${env.JENKINS_URL}"
	                echo "Jenkins JOB Number ${env.BUILD_NUMBER}"
	                echo "Jenkins JOB Name ${env.JOB_NAME}"
	                echo "GitHub BranhName ${env.BRANCH_NAME}"
	                checkout scm
	

	            }
	        }

	  stage('installPlat') {
	            steps {
	                echo "Building..with C:\\ProgramData\\Jenkins\\.jenkins\\workspace"
	                UiPathInstallPlatform (
					   cliNupkgPath: 'C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Uipath_Jenkins_Latest_main\\UiPath.CLI.Windows.22.10.8438.32859.nupkg',
					   cliVersion: 'WIN_22.10.8438.32859',
					   forceInstall: true,
					   traceLevel: 'None'
					)
	            }
	        }

	         // Build Stages
	        stage('Testrun') {
	            steps {
	                UiPathTest(
                                timeout: 10000,
			        folderName: 'Modren Example',
 				orchestratorAddress: 'https://desktop-dkphe2o/',
				orchestratorTenant: 'Default', 
				parametersFilePath: '', 
				testResultsOutputPath: '', 
				testTarget: TestSet('Coverage_new'), 
				traceLevel: 'None',
				credentials: UserPass('cb0fbc79-b4f7-46d4-8f60-74efbefbe4f2'),
	        )
	            }
	        }
	         

	}

	}