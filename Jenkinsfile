import com.hotmart.pipeline.Util

node{

    	stage('Download') {
        downloadRepo {
            name = 'user-agent-utils'
            branch = 'master'
        }
    }
    
    dir('user-agent-utils'){
	    stage('Build') {
	        mvn {
	            command = 'clean install -DskipTests -U'
	        }
	    }
	    stage('Test') {
	        mvn {
	            command = 'org.jacoco:jacoco-maven-plugin:prepare-agent surefire:test'
	            archiveArtifacts = true
	        }
	    }
	    stage("Artifactory") {
	       artifactory {}
	    }
    }
}