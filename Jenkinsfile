pipeline {
  triggers {
    pollSCM ('* * * * *')
  }
  agent {
    node {
      label 'nodejs'
    }
  }
  stages {
    stage ('Validate configuration resources') {
      steps {
        sh 'oc apply --dry-run --validate -f config'
      }
    }
    stage ('Apply resources') {
      when {
        branch 'main'
      }
      steps {
        sh 'oc apply -f config'
      }
    }
  }
}
