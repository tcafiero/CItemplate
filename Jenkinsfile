pipeline {
  agent {
    node {
      label 'toolchain'
    }

  }
  stages {
    stage('Build') {
	when {
	branch 'develop'
	}
      steps {
        echo 'Build'
      }
    }
    stage('Stage') {
	when {
	branch 'stage'
	}
      steps {
        echo 'Stage'
        input(message: 'There is a candidate version, procede to release', ok: 'YES', id: 'tcafiero')
      }
    }
    stage('Release') {
	when {
	branch 'master'
	}
      steps {
	    echo 'Master'
      }
    }
  }
}