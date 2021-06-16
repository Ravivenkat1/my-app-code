
node {
   def mvn = tool name: 'maven', type: 'maven'
   stage('SCM Checkout'){
    // Clone repo
	git 'https://github.com/srikanthweb/my-app-code.git'
   
   }	
   stage('compile package'){
	   // Build using maven
	   
	   sh "${mvn}/bin/mvn package"
   }
stage('SonarQube Analysis') {
        withSonarQubeEnv('sonar-6') { 
          sh "${mvn}/bin/mvn sonar:sonar"
        }
    }
	stage('Email Notification'){
	mail bcc: '', body: 'maven build is success full', cc: '', from: '', replyTo: '', subject: 'build package ', to: 'gsri1190@gmail.com'
		
	}
	stage('Slack Notification'){
		//slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#dev-sri', color: 'good', message: 'build successfully finished', teamDomain: 'vprofile-projects', tokenCredentialId: 'slack-dev-sri', username: 'srikanth'
		//slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#dev-sri', color: 'good', message: 'build successfully finished', teamDomain: 'vprofile-projects', tokenCredentialId: 'slack_notification', username: 'srikanth'
	slackSend baseUrl: 'https://hooks.slack.com/services/', botUser: true, channel: '#dev-sri', color: 'good', message: 'build successfully finished', teamDomain: 'vprofile-projects', tokenCredentialId: 'slack-dev-sri', username: 'srikanth'
	}
	
	
}

