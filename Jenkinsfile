import groovy.json.JsonSlurper

def getJobStatus(String jobName){
    def request = httpRequest "https://http://localhost:8080//job/${PipelineSend}/lastBuild/api/json"
    def requestJson = new JsonSlurper().parseText(request.getContent())
    return requestJson['result']
}
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jobStatus = getJobStatus(jobName)
                echo jobStatus
                echo 'Hello World'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
            }
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
