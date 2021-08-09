pipeline {
  agent kurhah.dmz
  parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
  stages {
    stage("build") {
	  steps {
	    echo "${params.Greeting} World!" 
      }
	}

    stage("test") {
	  steps {
	  }
	}
    stage("deploy") {
	  steps {
	  }
	}

  }
}
