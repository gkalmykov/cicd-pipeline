pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('image build') {
      steps {
        sh 'docker build -t "pipelineimage"'
      }
    }

  }
}