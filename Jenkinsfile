pipeline{
  agent any
  stages{
    stage('Checkout the code from SCM'){
      steps{
        echo 'code has been checkout'
      }
    }
    stage('Building the Project'){
      steps{
        echo 'Building the Project'
        sh 'mvn clean install -DskipTests'
      }
    }
    stage('building the docker image'){
      steps{
        echo 'build the docker image'
        sh 'docker build -t mobilestore .'
      }
    }
    stage('deploying in to dev env'){
      steps{
        echo 'Deployment to the developer enviroment'
        sh 'docker run -d --name=mobilestore -p 8099:8099 mobilestore'
      }
    }
  }
}