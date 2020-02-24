pipeline {
  agent any
  stages {
    stage('Compile') {
       steps {
	        sh "mvn compile"
       }
    }

    stage('Build') {
	     steps {
          sh "mvn package"
	     }
    }

    stage('Install') {
	     steps {
          sh 'mvn install'
	     }
    }

    stage('Archieve') {
        steps {
           archiveArtifacts 'target/*.jar'
        }
    }

    stage('FingerPrint') {
        steps {
           fingerprint 'target/*.jar'
        }
    }
    stage ('Notify'){
        steps {
        mail bcc: '', body: '''Please check the build "shopping cart" in jenkins. its failed

Team jenkins''', cc: '', from: '', replyTo: '', subject: 'Build has failed , Please check', to: 'mailabdulaali@gmail.com'
        }  
    }
    stage('HTML_Publish') {
	     steps {
	         junit 'target/surefire-reports/TEST-*.xml'
        }
    }

  }

}
