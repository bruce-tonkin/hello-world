node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr', description: 'What environment should this be run against?')
      string(name: 'APP', defaultValue: 'fcbc', description: 'Which component do you want to deploy?')
      string(name: 'gitTag', defaultValue: 'master', description: 'The repository version to pull from')      
    }
    
    switch (ENV) {
        case "Delivery":
          echo "Building dlvr"
          env.SDLC = 'dlvr'
        break
        case "Test":
          echo "Building test"
          env.SDLC = 'test'
        break
        case "Production":
          echo "Building prod"
          env.SDLC =  'prod'
        break
        default: 
          println "That was unexpected with variable ENV"
    }
    
    switch (APP) {
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
 
    
    echo "This is my echo with ENV: ${env.SDLC}"
    echo "This is my echo with APP: ${env.APP}"
    echo "This is my echo with gitTag: ${gitTag}"
    
    echo "Set variables that can be used in external processes"
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
