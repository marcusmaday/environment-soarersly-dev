pipeline {
  agent any
  environment {
    DEPLOY_NAMESPACE = "jenkins-x"
  }
  stages {
    stage('Validate Environment') {
      steps {
        dir('env') {
          sh 'jx step helm build'
        }
      }
    }
    stage('Update Environment') {
      when {
        branch 'master'
      }
      steps {
        dir('env') {
          sh 'jx step env apply'
        }
      }
    }
  }
}
