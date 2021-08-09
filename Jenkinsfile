node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr', description: 'What environment should this be run against?')
    }  
    switch (ENV) {
        case "Delivery":
          echo "Building dlvr"
          env.SDLC = 'dlvr'
          echo "Building delivery" ${env.SDLC}
        break
        case "Test":
          echo "Building test"
          env.sdlc = 'test'
        break
        case "Production":
          echo "Building prod"
          env.sdlc =  'prod'
        break
        default: 
          println "That was unexpected"
    }
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
