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
          }
      }
    }
    
    stage('Deploy') {
      steps {
        script {
          testScript.test_source('max')
        }
      }
    }
  }
}
