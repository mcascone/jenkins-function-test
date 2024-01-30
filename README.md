# How I'm discovering if local files can be loaded as vars (to be used as functions)

1. Create the pipeline in a test repo
2. create a simple jenkins file to load the files
3. test various configurations:
   1. `load('src/test.groovy')`
   1. `load('vars/test.groovy')`

## Results

It can be done!  The files can be loaded as vars and used as functions.

There are some tricks/caveats:

1. The script must end with `return this`
1. Unless the var is defined prior to the pipeline block, it will go out of scope like any other var when its scope closes.

    ```groovy
    steps {
      script {
        def testScript = load('src/test_src.groovy')
      }
    }
    ```

    `testScript` will go out of scope when the `script` block closes.

  Instead, define the var prior to the pipeline block:

  ```groovy
      def testScript

      pipeline {
        agent any
        stages {
          stage('test') {
            steps {
              script {
                testScript = load('src/test_src.groovy')
              }
            }
          }
        }
      }
  ```

2. The file must be loaded, and subsequently used, in `script` blocks.
3. You can define a `call()` function and call it with the name of the script.
  
    ```groovy
    def call() {
      echo 'this is a call'
    }
    ```

    ```groovy
    script {
      testScript()
    }
    ```

4. You can also use class members inline:
  
    ```groovy
    script {
      def aValue = load('src/test_src.groovy').aFunction()
    }
    ```


## Conclusion

This is a viable way to load local files as vars and use them as functions.  It's not as clean as loading them as shared libraries, but it's a good option for small, simple functions that don't need to be shared across multiple pipelines.