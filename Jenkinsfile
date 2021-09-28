pipeline {
  agent any
  stages {
    stage('PreDep') {
      parallel {
        stage('PreDep') {
          steps {
            sh 'git --version'
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
ls -al 
scp nginx.yaml root@172.18.0.6:/ 
ssh root@172.18.0.6 kubectl apply -f /nginx.yaml'''
      }
    }

    stage('PostDeploy') {
      steps {
        writeFile(file: 'status.txt', text: 'Process Completed')
      }
    }

  }
}