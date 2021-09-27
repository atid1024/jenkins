pipeline {
  agent any
  stages {
    stage('PreDep') {
      parallel {
        stage('PreDep') {
          steps {
            sh '''git --version
java -v
mvn --version'''
          }
        }

        stage('FileCheck') {
          steps {
            fileExists 'nginx.yaml'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        sh 'ls -al'
      }
    }

    stage('PostDeploy') {
      steps {
        writeFile(file: 'status.txt', text: 'This is Working')
      }
    }

  }
}