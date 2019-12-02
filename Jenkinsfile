
node {
   def sonarUrl = 'sonar.host.url=http://172.31.30.136:9000'
   def mvn = tool (name: 'maven3', type: 'maven') + '/bin/mvn'
   stage('SCM Checkout'){
    // Clone repo
//	git branch: 'master', 
//	credentialsId: 'github', 
	url: 'https://github.com/navaneswar/myweb'
   
   }
     
	
   stage('Mvn Package'){
	   // Build using maven
	   
	   sh "${mvn} clean package deploy"
   }
   
 
   stage('Email Notification'){
		mail bcc: '', body: """Hi Team, You build successfully deployed
		                       Job URL : ${env.JOB_URL}
							   Job Name: ${env.JOB_NAME}

Thanks,
DevOps Team""", cc: '', from: '', replyTo: '', subject: "${env.JOB_NAME} Success", to: 'navaneswar@gmail.com'
   
   }
}

