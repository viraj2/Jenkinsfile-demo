node {
	def workSpaceHome = pwd()
    stage('Checkout') {
        checkout scm
    }
    stage('Build') {    
		maven= tool 'Maven 3.5.3'
		if (isUnix()) {
			sh "${maven}/bin/mvn test"
		}
		else{
			bat "${maven}\\bin\\mvn test"
		}	
    }
	stage('QTMUploadResult'){
		load(workSpaceHome + "/config.groovy")
		step([$class: 'QTMReportPublisher', qtmUrl: ${baseUrl}, automationFramework: 'TESTNG', testResultFilePath: 'testng/testng-results.xml', qtmAutomationApiKey: '${apikey}', project: 'MPT', release: 'Release 1', cycle: 'Cycle 1', buildName: 'testBuild1', platformName: 'Jenkins'])
	}
}
