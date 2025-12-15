pipeline {
  agent any

  environment {
    SAFETY_API_KEY = 'YOUR_API_KEY'
  }

  stages {
    stage('Install Safety') {
      steps {
        sh '''
          pip install --upgrade pip --break-system-packages
          pip install safety --break-system-packages
        '''
      }
    }

    stage('Safety Scan') {
      steps {
        sh '''
          echo "=============================="
          echo " Running Safety Dependency Scan"
          echo "=============================="
          safety scan -r requirements.txt || true
          echo "=============================="
          echo " Scan completed"
          echo "=============================="
        '''
      }
    }
  }
}

