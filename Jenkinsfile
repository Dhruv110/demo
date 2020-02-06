

pipeline {
	agent any
	
	stages{
		stage('checkout'){
			steps{
				echo 'checkout stage'
				git 'https://github.com/Dhruv110/demo.git'
			}
		}
		stage('Build'){
			steps{
				echo 'Build stage'
				sh '/Users/dhruv/Desktop/DevOps/apache-maven-3.6.3/bin/mvn package -f /Users/dhruv/.jenkins/workspace/Demo/sample/pom.xml'
			}
		}
		stage('Test'){
			steps{
				echo 'Test stage'
			}
		}
		stage('Artifact upload'){
			steps{
				echo 'Artifact Upload stage'
				nexusArtifactUploader artifacts: [[artifactId: 'sample', classifier: '', file: '/Users/dhruv/.jenkins/workspace/Demo/sample/target/sample-1.1-SNAPSHOT.jar', type: 'jar']], groupId: 'com.my', nexusUrl: 'localhost:8081/nexus', nexusVersion: 'nexus3', protocol: 'http', repository: 'snapshots', version: '1.1-SNAPSHOT'
	    
			}
		}
		stage('Deploy'){
			steps{
				echo 'Deploy stage'
				sh 'cp /Users/dhruv/.jenkins/workspace/Demo/sample/target/sample-1.1-SNAPSHOT.jar  /Users/dhruv/Desktop/DevOps/apache-tomcat-9.0.30/webapps/'
			}
		}
	
	}
}
