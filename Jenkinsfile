import groovy.json.JsonSlurper

def getJobStatus(String jobName){
    def request = httpRequest "https://http://localhost:8080//job/${jobName}/lastBuild/api/json"
    def requestJson = new JsonSlurper().parseText(request.getContent())
    return requestJson['result']
}
node() {
    def any_success = false
    stage('check'){
        for(jobname in ['PipelineSend']){
            jobStatus = getJobStatus(jobName)
            echo jobStatus
            if(jobStatus == "SUCCESS" || jobStatus == "UNSTABLE"){
                any_success = true
                break
            }
        }
    }
    stage('report') {
        echo 'Hello'
    }


}
