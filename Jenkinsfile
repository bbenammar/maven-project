pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/bbenammar/maven-project.git'
      }
    }

    stage('build') {
      parallel {
        stage (build){
          stages{
        stage('build') {
          steps {
            bat 'echo docker build'
          }
        }
    stage('publish') {
      steps {
        bat 'echo docker push'
      }
    }
        }
        }
        stage('scan') {
          steps {
            bat 'echo scan sonnar'
          }
        }

      }
    }



    stage('deploy to build') {
      parallel {
        stage('deploy to build') {
          steps {
            bat 'echo deploy 1'
          }
        }

        stage('deploy RE7') {
          steps {
            bat 'echo re7'
          }
        }

      }
    }

  }
  parameters {
    string(name: 'tomcat_dev', defaultValue: '35.166.210.154', description: 'Staging Server')
    string(name: 'tomcat_prod', defaultValue: '34.209.233.6', description: 'Production Server')
  }
  triggers {
    pollSCM('* * * * *')
  }
}
