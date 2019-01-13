node() {
  try {
stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  bat 'mvn package'
}
    
     stage("SonarQube analysis") {
            withSonarQubeEnv('Sonar') {
               bat 'mvn sonar:sonar'
            }    
    }
    
    stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  emailext attachLog: true, body: 'Sonar Quality Gate has been failed', compressLog: true , subject: 'Jenkins Build Failure', to: 'akshay.inlondon@gmail.com'
              }
          }
      }      
    
  } catch (err) {
    emailext attachLog: true, body: 'Jenkins build has been failed', compressLog: true , subject: 'Jenkins Build Failure', to: 'akshay.inlondon@gmail.com'
  }
}
