node {

    checkout scm
    bat 'mvn test'
    step([$class: 'TestReportDeployPublisher',testToRun: 'CLOUD', apikey: 'dsvgdg', format: 'testng/xml', file: '\\testng', testassethierarchy: 'TestScenario-TestCase', labels: 'label', version: 'version', jirafields: '["abc","cde"]'])

}
