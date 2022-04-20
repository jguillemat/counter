/* =================================================================
 * Essi Projects - Maven Standard Jenkins Pipeline
 *
 * @author: jguillemat@essiprojects.com
 * ================================================================= 
*/

pipeline {
    node("maven") {
	    stages {
		stage('SCM Checkout') {
		    steps {
			echo 'checkout from: '+env.BRANCH_NAME
			echo 'checkout from: '+env.GIT_BRANCH
			sh 'printenv'
			echo 'Git checkout ...'
			checkout scm 
		    }
		}
		stage('Clean') {
		    steps {
			echo 'Maven clean...'
			sh 'mvn -B clean'
		    }
		}
		stage('Package') {
		    steps {
			echo 'Maven package...'
			sh 'mvn -B package'
		    }
		}
		stage('Deploy to Nexus') {
		    steps {
			echo 'Maven deploy to Nexus...'
			sh 'mvn -B deploy'
		    }
		}
		/*
		stage('Deploy to WLS') {
		    steps {
			echo 'Maven pre-integration-test ( weblogic profile )...'
			sh 'mvn -B pre-integration-test -P weblogic'
		    }
		}
		*/
	    }
    }
}

