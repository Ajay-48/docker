def dockerImageTag = "ajay048/mydockerrepo:v${BUILD_NUMBER}"
node{
  stage('Checkout') {
      git branch: 'main', url: 'https://github.com/Ajay-48/docker.git'
  }
  stage ('DockerImageBuild') {
    def dockerImage = docker.build(dockerImageTag)
  }
  stage ('PushToDockerHub') {
    docker.withRegistry('https://registry.hub.docker.com', 'docker'){
      def dockerImage = docker.image(dockerImageTag)
      dockerImage.push()
    }
  }
}
