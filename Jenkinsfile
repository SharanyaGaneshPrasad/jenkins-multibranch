pipeline {
  agent any

  stages {
    stage('Say Hello') {
      steps {
        echo "Hello from the feature branch!"
        sh 'echo "This is feature branch: ${env.BRANCH_NAME}"'
      }
    }

    stage('Pause For Input') {
      steps {
        script {
          input message: "Feature branch: continue?", ok: "Yes, continue"
        }
      }
    }
  }

  post {
    always { echo "Feature branch pipeline done." }
  }
}
