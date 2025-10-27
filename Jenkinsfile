pipeline {
  agent any

  triggers {
    // run the pipeline every 10 minutes (use small interval for demo)
    // change as needed. H/10 * * * * = roughly every 1 minutes
    cron('H/1 * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        echo "Checking out source"
        checkout scm
      }
    }

    stage('Build') {
      steps {
        echo "Building (simulated)"
        sh 'echo build-step'
      }
    }

    stage('Pre-Deploy Approval') {
      steps {
        script {
          // input step pauses the pipeline and awaits user action in Jenkins UI
          def userInput = input(
            message: "Approve deployment?",
            ok: "Deploy now",
            parameters: [
              string(name: 'RELEASE_NOTE', defaultValue: 'No notes', description: 'Enter release notes (optional)')
            ]
          )
          echo "User approved with note: ${userInput}"
        }
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying (simulated)"
        sh 'echo deploy-step'
      }
    }
  }

  post {
    success { echo "Pipeline completed SUCCESS" }
    failure { echo "Pipeline FAILED" }
  }
}
