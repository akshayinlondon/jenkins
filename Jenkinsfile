node {

stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  sh 'mvn package'
}

}
