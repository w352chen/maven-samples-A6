pipeline {
  agent any
  tools { 
      maven 'DHT_MVN' 
      jdk 'DHT_SENSE' 
  }
  stages {
    stage('Git Bisect') {
      steps {
        sh 'git bisect start'
        sh 'git bisect bad 198644632661c67b6c32f59e9047c11a70685e15'
        sh 'git bisect good 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5'
        sh 'bisect run mvn clean test'
        sh 'git bisect reset'
      }
    }
  }
}
