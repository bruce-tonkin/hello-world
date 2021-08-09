node ('geoservertest') {
  try {
    parameters {
      string(name: 'SDLC', defaultValue: 'dlvr', description: 'What environment should this be run against?')
    }  
    switch (ENV) {
      case "dlvr":
        echo "Building dlvr"
      break
      case "test":
        echo "Building test"
      break
      case "prod":
        echo "Building prod"
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
                throw e
    }
}
