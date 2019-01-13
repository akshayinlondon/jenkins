node() {
  try {
stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  bat 'mvn package'
}   
  } catch (err) {
    emailext attachLog: true, body: 'Jenkins build has been failed', compressLog: true , subject: 'Jenkins Build Failure', to: 'akshay.inlondon@gmail.com'
  }
}
