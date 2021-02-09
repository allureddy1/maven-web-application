pipeline{
  agent any
  environment{
    def mavenHome=tool name: "maven3.6.3"

  }
   stages{
    stage('checkout the code'){
        steps{
            git credentialsId: 'github credentials', url: 'https://github.com/allureddy1/maven-web-application.git'
        }
    }
    stage('Build the code'){
        steps{
           sh "${mavenHome}/bin/mvn clean package"
        }
    }
    stage('Genrate SonarQube Report'){
        steps{
          sh "${mavenHome}/bin/mvn sonar:sonar"
        }
    }
    stage('Deploy the artifact into nexus'){
        steps{
            sh "${mavenHome}/bin/mvn deploy"
        }
    }
  }
}
