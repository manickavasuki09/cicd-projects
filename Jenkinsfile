pipeline {
  agent any
    // Use any agent that has Docker and the shell executor installed
    
    // Or restrict by label/tag, e.g.: label 'shell'
  

  stages {
    stage('build') {
      steps {
        script {
          echo 'Building Docker image...'
          // Build image tagged gitlab-demo from current directory
          sh 'docker build -t demo .'
        }
      }
    }

    stage('deploy') {
      steps {
        script {
          echo 'Deploying container...'

          // Stop existing container if it exists, ignore errors
          sh 'docker stop demo || true'

          // Remove existing container if it exists, ignore errors
          sh 'docker rm demo || true'

          // Run new container in detached mode, name it demo,
          // map host port 8080 -> container port 80
          sh 'docker run -d --name demo -p 8080:80 demo'
        }
      }
    }
  }

  post {
    always {
      // Optional: print container status at the end
      script {
        echo 'Container status:'
        sh 'docker ps -a --filter name=demo'
      }
    }
  }
}
