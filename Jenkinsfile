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
  }
}