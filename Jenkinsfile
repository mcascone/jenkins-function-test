pipeline {
  agent any
  
  stages {
    // stage('Build') {
    //   steps {
        // load('src/test_src.groovy')
        // test_src('max')
        // this doesn't work
    //   }
    // }
    
    stage('Test') {
      steps {
        load('vars/test_src.groovy')
        test_src('max')
      }
    }
    
    // stage('Deploy') {
    //   steps {
    //     // TODO: Add deployment steps here
    //   }
    // }
  }
}
