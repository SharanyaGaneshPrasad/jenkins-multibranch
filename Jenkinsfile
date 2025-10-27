pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        echo "Checking out the repo (feature branch)..."
        checkout scm
      }
    }

    stage('Say Hello') {
      steps {
        echo "Hello from the feature branch!"
        sh """
          echo "This is the feature branch: ${env.BRANCH_NAME}"
        """
      }
    }

    stage('Pause For Input') {
      steps {
        script {
          // Pauses the pipeline; user must click "Yes, continue"
          input message: "Feature branch: continue?", ok: "Yes, continue"
        }
      }
    }

    stage('Finish') {
      steps {
        echo "Feature branch pipeline finished"
        sh """
          echo "Feature branch ${env.BRANCH_NAME} - done"
        """
      }
    }
  }

  post {
    always { echo "Feature pipeline completed" }
  }
}
