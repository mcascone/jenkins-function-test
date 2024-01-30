// define the script var outside the pipeline, so it is in global scope
def testScript

pipeline {
  agent any
  
  stages {
    stage('Test') {
      steps {
          script {
            testScript = load('src/test_src.groovy')
          }
      }
    }
    
    stage('Deploy') {
      steps {
        script {
          testScript.test_source('max')
          testScript()
        }
      }
    }
  }
}
