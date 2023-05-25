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
    stage('codequality analyzing'){
      steps{
        sh '''
        mvn clean verify sonar:sonar \
          -Dsonar.projectKey=Mobilestore \
          -Dsonar.projectName='Mobilestore' \
          -Dsonar.host.url=http://20.12.44.193:9000 \
          -Dsonar.token=sqp_88cb3f7b4cebf083bfd4b4ccf8bac8adf2f63d31
          '''
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
        sh 'docker rm -f mobilestore || true '
        sh 'docker run -d --name=mobilestore -p 8099:8099 mobilestore'
      }
    }
  }
}