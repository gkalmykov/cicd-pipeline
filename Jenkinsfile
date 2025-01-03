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
        sh 'docker build -t cicdplimage:latest .'
      }
    }

    stage('Docker publish') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', dockerhub_id)

          {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
          }
        }

      }
    }

  }
  environment {
    registry = 'gkalmykov/cicd-pipeline'
    registryCredentials = 'dockerhub_id'
  }
}