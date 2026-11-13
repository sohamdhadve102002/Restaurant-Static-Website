pipeline {
  agent any

  stages {

    stage('Github Connection Test'){
      steps {
        git branch: 'main',
        credentialsId: 'Restaurant-Website-Key',
        url: 'https://github.com/sohamdhadve102002/Restaurant-Static-Website.git'

        echo "Github Connection Test Successful"
      }
    }

    stage('Check all Files'){
      steps {
       sh 'ls -la'
      }
    }


  }
}