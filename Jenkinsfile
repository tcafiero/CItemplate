pipeline {
  agent {
    node {
      label 'toolchain'
    }
  }
  triggers { pollSCM('*/1 * * * *') }
  stages {
    stage('Build') {
      when {
        branch 'develop'
      }
      options {
        timeout(time: 10, unit: 'MINUTES') 
      }
      steps {
        echo 'Build'
		bat(script: '"C:\\CIexample\\workspace\\CIexample_develop\\Stages\\Building\\Build.cmd"')
      }
    }
    stage('Test') {
      when {
        branch 'develop'
      }
      options {
        timeout(time: 10, unit: 'MINUTES') 
      }
      steps {
        echo 'Test'
		bat(script: '"C:\\CIexample\\workspace\\CIexample_develop\\Stages\\Testing\\Test.cmd"')
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