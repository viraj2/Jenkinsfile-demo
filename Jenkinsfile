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
		step([$class: 'QTMReportPublisher', qtmUrl: "${baseUrl}", automationFramework: "${framework}", testResultFilePath: "${filepath}", qtmAutomationApiKey: "${apikey}", project: "${project}", release: "${release}", cycle: "${cycle}", buildName: "${build}", platformName: "${platform}"])
	}
}
