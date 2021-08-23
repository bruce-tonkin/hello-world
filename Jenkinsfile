node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr', description: 'What environment should this be run against?')
      string(name: 'APP', defaultValue: 'fcbc'), description: 'Which component do you want to deploy?')
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
          println "That was unexpected"
    }
    echo "This is my echo with ${env.SDLC}"
    echo "gitTag is ${gitTag}"
    
    echo "Set variables that can be used in external processes"
    setEnv ([
      "GIT_SSL_NO_VERIFY=true",
      "FOLDERNAME=ecocat_${env.PUBORSEC}",
      "SITENAME=ecocat",
      "PUBORSEC=${env.PUBORSEC}", 
      "APPSERVER=${env.APPSERVER}",
      "SDLC=${env.SDLC}"
    ])
    
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
