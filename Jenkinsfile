pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	git url: 'https://github.com/Tharun4153/gamukart.git',
				branch: 'master'
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
	stage('Deploy') {
	   steps {
	    sshagent(['ssh-key-for-deploy']) {
		sh 'scp -o StrictHostKeyChecking=no target/gamutkart.war root@172.31.47.153:/opt/tomcat/webapps'
	    }
	}
    }
}
}
