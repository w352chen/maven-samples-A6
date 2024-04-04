pipeline {
  agent any
  stages {
    stage('check out') {
      steps {
        git(url: 'https://github.com/w352chen/maven-samples-A6.git', branch: 'master')
      }
    }

    stage('Git Bisect') {
      steps {
        sh 'git bisect start'
        sh 'git bisect bad 198644632661c67b6c32f59e9047c11a70685e15'
        sh 'git bisect good 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5'
        sh '''
            git bisect run bash -c \'
            if mvn clean test; then
              exit 0
            
else
              exit 1
            fi
            \'
        '''
      }
    }

  }
  tools {
    maven 'DHT_MVN'
    jdk 'DHT_SENSE'
  }
}