pipeline {
  agent any
  
  stages {
    // stage('Build') {
    //   steps {
    //     checkout scm
    //   }
    // }
    
    stage('Test') {
      steps {
          script {
            def testScript = load('src/test_src.groovy')
            testScript.test_source('max')
          }
      }
    }
    
    // stage('Deploy') {
    //   steps {
    //     // TODO: Add deployment steps here
    //   }
    // }
  }
}
