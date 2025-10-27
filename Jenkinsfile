pipeline {
  agent any

  // Demo cron trigger: runs every 2 minutes for classroom testing.
  // Replace with production-friendly schedule when needed.
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
        echo "Build (demo) - prepare artifacts here"
        // Use Groovy triple-quoted string so ${env.BRANCH_NAME} is interpolated
        sh """
          echo "Running demo build on branch ${env.BRANCH_NAME}"
        """
      }
    }

    stage('Manual Approval') {
      steps {
        script {
          // Pauses the pipeline waiting for manual approval
          input message: "Approve deployment for branch ${env.BRANCH_NAME}?", ok: "Proceed"
        }
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploy stage: simulating deployment"
        sh """
          echo "Deployment successful on branch ${env.BRANCH_NAME}"
        """
      }
    }
  }

  post {
    success { echo "Pipeline finished SUCCESS" }
    failure { echo "Pipeline finished FAILURE" }
    always  { echo "Pipeline run complete" }
  }
}
