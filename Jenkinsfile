import groovy.json.JsonSlurper

def getJobStatus(String jobName){
    def request = httpRequest "https://http://localhost:8080//job/${jobname}/lastBuild/api/json"
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
            steps {
                for(jobname in ['PipelineSend']){
                    jobStatus = getJobStatus(jobName)
                    echo jobStatus
                }
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
