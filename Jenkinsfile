pipeline {
  agent any

  // Demo cron trigger: runs every 2 minutes for classroom testing.
  // In production use a longer schedule (e.g. H H * * *).
  triggers {
    cron('H/2 * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        echo "Checking out the repo..."
        checkout scm
      }
    }

    stage('Build') {
      steps {
        echo "Building (demo step) - compile or prepare artifacts here"
        sh 'echo "build step: nothing to build for this demo"'
      }
    }

    stage('Manual Approval') {
      steps {
        // The input step pauses the pipeline and waits for a user to click "Proceed"
        script {
          input message: "Approve deployment?", ok: "Proceed"
        }
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploy stage: simulating deployment"
        sh 'echo "Deployment successful on branch ${env.BRANCH_NAME}"'
      }
    }
  }

  post {
    success { echo "Pipeline finished SUCCESS" }
    failure { echo "Pipeline finished FAILURE" }
  }
}
