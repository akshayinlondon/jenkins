node {
  try {
stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  def mvnHome = tool name: 'mvn', type: 'maven'
  bat "${mvnHome}/bin/mvn package"
}
    
 stage("SonarQube analysis") {
   def mvnHome = tool name: 'mvn', type: 'maven'
            withSonarQubeEnv('Sonar') {
               bat "${mvnHome}/bin/mvn sonar:sonar"
            }    
    }
    
    stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
      }        
    
  } catch (err) {
    emailext body: 'Jenkins build has been failed', compressLog: true , subject: 'Jenkins Build Failure', to: 'akshay.inlondon@gmail.com'
  }
}
