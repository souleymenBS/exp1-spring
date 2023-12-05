pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ('Clean up') {
      steps {
        deleteDir()
      }
    }
    stage ('Clone repo') {
      steps {
        sh "git clone https://github.com/souleymenBS/exp1-spring.git"
      }
    }
    stage('Build') {
      steps {
        dir("exp1-spring") {
          sh "mvn clean install"
        }
      }
    }
    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonar-server') {
          dir("exp1-spring") {
            sh "mvn sonar:sonar"
          }
        }
      }
    }
  }
}
