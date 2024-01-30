# How I'm discovering if local files can be loaded as vars (to be used as functions)

1. Create the pipeline in a test repo
2. create a simple jenkins file to load the files
3. test various configurations:
  1. `load('src/test.groovy')`
  2. `load('vars/test.groovy')`
