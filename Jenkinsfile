import groovy.json.JsonSlurper

def getJobStatus(String){
    def request = httpRequest "https://http://localhost:8080//job/PipelineSend/lastBuild/api/json"
    def requestJson = new JsonSlurper().parseText(request.getContent())
    return requestJson['result']
}
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build') {
                jobStatus = getJobStatus()
                echo jobStatus
                echo 'Building'
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
