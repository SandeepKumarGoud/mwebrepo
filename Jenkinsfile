pipeline {
agent any
environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('code checkout ')
	    {
            	steps 
		    {
			git credentialsId: 'git_credential', url: 'https://github.com/SandeepKumarGoud/mwebrepo.git'
                      echo 'stage 1.'
            	     }
	     }
 stage('code build ')
	    {
            	steps 
		    {
              sh 'mvn clean install'
			echo 'stage 2'
              }
	     }
 stage('code deploy ')
	    {
            	steps 
		    {
			sshagent(['deploy_user'])
			{
   		      sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war  ec2-user@52.38.89.123:/opt/apache-tomcat-9.0.62/webapps"
			}
                      echo 'stage 3.'
             }
	     }
    }
}
