// pipeline {
//   agent any

//   stages {

//     stage('Github Connection Test'){
//       steps {
//         git branch: 'main',
//         credentialsId: 'Restaurant-Website-Key',
//         url: 'https://github.com/sohamdhadve102002/Restaurant-Static-Website.git'

//         echo "Github Connection Test Successful"
//       }
//     }

//     stage('Check all Files'){
//       steps {
//        sh 'ls -la'
//       }
//     }

//   }
// }


pipeline {
  agent any

  stages {
    
    // Step 1 : Get Latest Code from Github
    stage('Latest code from Github'){
      steps {
        checkout scm
        echo "code downloaded from Github"
      }
    }

    // Step 2 : Check Required Files
    stage('Check Required Files'){
      steps {
        sh 'ls -la'
        sh 'test -f index.html'
        sh 'test -f Dockerfile'

        echo "Required Files are Present"
      }
    }

    // Step 3 : Build Docker Image
    stage('Docker Build'){
      steps {
        sh 'docker build -t restaurant-website:latest .'
        echo "Docker Image Built Successfully"
      }
    }

    // Step 4 : Run Docker Container
    stage('Deployment'){
      steps{
        //Remove old container if exists
        sh 'docker rm -f restaurant-website || true'

        //Run new container
        sh 'docker run -d -p 80:80 --name restaurant-website restaurant-website:latest'

        echo "Website Deployed Successfully"

      }
    }  

  }


}