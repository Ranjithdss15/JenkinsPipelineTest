import groovy.json.JsonSlurperClassic

node('master') {

  stage("test"){
  
  echo "stage 1"
  }
stage ("local")
{
def buildNumber = Jenkins.instance.getItem('getBuildNumber').lastSuccessfulBuild.number
print buildNumber
  }

stage("url")
{
httpRequest url: 'https://35.168.32.83:8080/job/Build/api/json', outputFile: 'output.json'
def jsonFile = readFile(file: 'output.json')
def data = new JsonSlurperClassic().parseText(jsonFile)
latestBuildNumber = "${data.lastSuccessfulBuild.number}"
print latestBuildNumber
}

}
