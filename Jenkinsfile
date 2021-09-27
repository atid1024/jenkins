pipeline {
  agent any
  stages {
    stage('PreDep') {
      parallel {
        stage('PreDep') {
          steps {
            sh '''git --version 
env'''
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
        sh '''echo $PWD
echo $USER'''
      }
    }

    stage('PostDeploy') {
      steps {
        writeFile(file: 'status.txt', text: 'This is Working')
      }
    }

  }
}