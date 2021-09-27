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
echo $HOME 
scp nginx.yaml root@172.18.0.6:/ 
ssh root@172.18.0.6 ls /'''
      }
    }

    stage('PostDeploy') {
      steps {
        writeFile(file: 'status.txt', text: 'This is Working')
      }
    }

  }
}