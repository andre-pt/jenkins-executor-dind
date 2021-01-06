#!groovy

def imagesByOrder = ["dind"]

def tagPrefix = "andrepm/jenkins-executor-"

node('docker') {

    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
        for (s in imagesByOrder) {
            def image = s
            stage("build " + image) {
                dir(image) {
                    def imageId = tagPrefix + image + ":latest"
                    sh "echo ${DOCKERHUB_PASSWORD} | docker login --password-stdin -u ${DOCKERHUB_USERNAME}"
                    sh "docker build . -t " + imageId
                    sh "docker push " + imageId
                }
            }
        }
    }
}