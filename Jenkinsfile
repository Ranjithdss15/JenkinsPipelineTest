import groovy.json.JsonSlurperClassic

node('master') {

  stage("test"){
  
  echo "stage 1"
  }
stage ("local")
{
  echo "lastSuccessfulBuild"
def buildNumber = Jenkins.instance.getItem('getBuildNumber_pipeline').lastSuccessfulBuild.number
print buildNumber
  }
  
stage ("Last Build")
  {
    echo "lastbuild"
  def lastbuild =  Jenkins.instance.getItem('getBuildNumber_pipeline').lastBuild.number
print lastbuild
    
     }
/*
stage("url")
{
httpRequest url: 'http://35.168.32.83:8080/job/Build/api/json', outputFile: 'output.json'
def jsonFile = readFile(file: 'output.json')
def data = new JsonSlurperClassic().parseText(jsonFile)
latestBuildNumber = "${data.lastSuccessfulBuild.number}"
print latestBuildNumber
}
*/

stage ("Invoke Pipeline")
  {

    echo "Invoke Pipeline"
    build job: 'getBuildNumber', parameters: [
                string(name: 'variable1', value: "from Pipeline") ]
  }
}
stage ("check")
{
  def lb = Jenkins.instance.getItem('getBuildNumber').lastBuild.number
  def lb1 = lb
  print lb1
  def sbn = Jenkins.instance.getItem('getBuildNumber').lastSuccessfulBuild.number
  print sbn
  if ( lb1 == sbn)
  {
  print "Successfully invoked"
  }
  else {
    print "failed"
  }
  
}
