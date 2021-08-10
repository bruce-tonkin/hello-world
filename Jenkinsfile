node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr', description: 'What environment should this be run against?')
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
