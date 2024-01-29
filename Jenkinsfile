pipeline {
  agent any
  
  stages {
    stage('Build') {
      steps {
        load('src/test_src.groovy')
        test_src('max')
      }
    }
    
    // stage('Test') {
    //   steps {
    //     // TODO: Add test steps here
    //   }
    // }
    
    // stage('Deploy') {
    //   steps {
    //     // TODO: Add deployment steps here
    //   }
    // }
  }
}
