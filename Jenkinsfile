import com.hotmart.pipeline.Util

node{
		stage('Download') {
		    downloadRepo {
		        name = 'user-agent-utils'
		        branch = 'master'
		    }
		}
		
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