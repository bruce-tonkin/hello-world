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
    setEnv ([
      "JOB_NAME=KML_BUILD",
      "GIT_SSL_NO_VERIFY=true",
      "APPSERVER=${env.APPSERVER}",
      "SDLC=${env.SDLC}"
    ])
     
    echo "JOB_NAME: ${JOB_NAME}"
    echo "GIS_SSL_NO_VERIFY: ${GIS_SSL_NO_VERIFY}"
    echo "APPSERVER: ${APPSERVER}"
    echo "SDLC: ${SDLC}"
    
//    setEnv ([
//      "GIT_SSL_NO_VERIFY=true",
//      "FOLDERNAME=ecocat_${env.PUBORSEC}",
//      "SITENAME=ecocat",
//      "PUBORSEC=${env.PUBORSEC}", 
//      "APPSERVER=${env.APPSERVER}",
//      "SDLC=${env.SDLC}"
//    ])
    
    stage ('SCM prepare'){
      echo 'Building Stage 1'
    }
  } catch (e) {
                currentBuild.result = "FAILED"
                notifyFailed()
                echo "Job Failes"
                throw e
    }
}
