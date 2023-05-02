pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout(scm: [$class: 'GitSCM', 
                          branches: [[name: '*/main']],
                          doGenerateSubmoduleConfigurations: false,
                          extensions: [[$class: 'CleanCheckout']],
                          submoduleCfg: [],
                          userRemoteConfigs: [[url: 'https://github.com/budhdhawan/Devops-.git']]], poll: true)
      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh 'sonar-scanner'
        }

      }
    }

  }
}