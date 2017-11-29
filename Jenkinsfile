node {
  def myGradleContainer = docker.image('gradle:jdk8-alpine')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  // mkdir  /var/jenkins_home/.gradle && chown 1000:1000
  stage('test') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && bash gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && bash gradlew run'
     }
  }
}
