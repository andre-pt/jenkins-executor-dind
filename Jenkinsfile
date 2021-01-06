#!groovy

def imagesByOrder = ["dind", "dind-java"]

def tagPrefix = "andrepm/jenkins-executor-"

node('docker') {
    git branch: 'main', credentialsId: 'github-password', url: 'https://github.com/andre-pt/jenkins-executor-dind.git'

    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
        for (s in imagesByOrder) {
            def image = s
            stage("build " + image) {
                dir(image) {
                    def imageId = tagPrefix + image + ":latest"
                    sh 'echo $DOCKERHUB_PASSWORD | docker login --password-stdin -u $DOCKERHUB_USERNAME'
                    sh "docker build . -t " + imageId
                    sh "docker push " + imageId
                }
            }
        }
    }
}