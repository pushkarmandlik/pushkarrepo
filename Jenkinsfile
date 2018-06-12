node {

stage ('SCM_checkout') {
	checkout([$class: 'GitSCM', 
		branches: [[name: '*/master']], 
		doGenerateSubmoduleConfigurations: false, 
		extensions: [], 
		submoduleCfg: [], 
		userRemoteConfigs: [[url: 'https://github.com/ganeshhp/helloworldweb.git']]])
	}

stage ('Build') {
	bat 'mvn clean package'
	}

stage ('archive') {
	archiveArtifacts 'target/*.war'
	}

stage ('deploy') {
	bat 'sh \'\'\'cp target/Helloworldwebapp.war /opt/apache-tomcat-8.5.21/webapps'
	bat '/opt/apache-tomcat-8.5.21/bin/shutdown.sh'
	bat '/opt/apache-tomcat-8.5.21/bin/startup.sh\'\'\''
	}

}
