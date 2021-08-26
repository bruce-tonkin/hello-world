node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr')
      string(name: 'APP', defaultValue: 'fcbc')
      string(name: 'APPSERVER', defaultValue: 'kurhah.dmz')
    }
    
    switch (KML_ENV) {
      case "Delivery":
        echo "Building dlvr"
        env.SDLC = 'dlvr'
        env.APPSERVER = 'kurhah.dmz'
        break
      case "Test":
        echo "Building test"
        env.SDLC = 'test'
        env.APPSERVER = 'kurhah.dmz'
        break
      case "Production":
        echo "Building prod"
        env.SDLC =  'prod'
        env.APPSERVER = 'imai.dmz'
        break
      default: 
        println "That was unexpected with variable ENV"
    }
    
    switch (KML_APP) {
      case "fcbc":
        echo "Building fcbc"
        env.APP = 'fcbc'
        break
      case "geocoder":
        echo "Building geocoder"
        env.APP = 'geocoder'
        break
      case "geomark":
        echo "Building geomark"
        env.APP =  'geomark'
        break
      case "Icons":
        echo "Building Icons"
        env.APP =  'Icons'
        break
      default: 
        println "That was unexpected with variable APP"
    }
    
    echo "This is my echo with env.SDLC: ${env.SDLC}"
    echo "This is my echo with env.APPSERVER: ${env.APPSERVER}"
    echo "This is my echo with env.APP: ${env.APP}"
    echo "This is my echo with KML_gitTag: ${KML_gitTag}"
    
    echo "Set variables that can be used in external processes"
    withEnv ([
      "JOB_NAME=kml-build",
      "GIT_SSL_NO_VERIFY=true",
      "APPSERVER=${env.APPSERVER}",
      "SDLC=${env.SDLC}",
      "gitTag=${KML_gitTag}"
    ])
    {
      echo "JOB_NAME: ${JOB_NAME}"
      echo "GIT_SSL_NO_VERIFY: ${GIT_SSL_NO_VERIFY}"
      echo "APPSERVER: ${APPSERVER}"
      echo "SDLC: ${SDLC}"
      echo "gitTag: ${gitTag}"
    
      stage ('SCM prepare'){
        echo 'Building Stage 1 - Check out source code'
//        deleteDir()
//        checkout([$class: 'GitSCM', branches: [[name: '${gitTag}']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'Default', submoduleCfg: [], userRemoteConfigs: [[credentialsId: '607141bd-ef34-4e80-8e7e-1134b7c77176', url: 'https://gogs.data.gov.bc.ca/waops/geoserver_build.git']]])

      }
      
      stage ('Build using Ant and copy configs to server'){
        echo 'Building Stage 2'
      }
      
    } // end of withEnv block
    
  } // end of try
  
  catch (e) {
    currentBuild.result = "FAILED"
    notifyFailed()
    echo "Job Fails"
    throw e
  } // end of catch
} // end of node

def notifyFailed() {
    emailext (
        subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
        body: """<html><body><p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
            <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p></html></body>""",
        to: 'bruce.tonkin@gov.bc.ca'
    )
} // end of def
