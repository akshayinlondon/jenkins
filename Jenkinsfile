node {

stage('SCM checkout') {
  git 'https://github.com/akshayinlondon/jenkins'
}

stage('complie-package') {
  def mvnHome = tool name: 'mvn', type: 'maven'
  bat "${mvnHome}/bin/mvn package"
}

}
