node {

stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  cmd 'mvn clean install'
}

}
