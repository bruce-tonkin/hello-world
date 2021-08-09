pipeline {
agent any
  parameters {
    string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    string(name: 'SDLC', defaultValue: '', description: 'What environment should this be run against?')
  }

  stages {
    stage("build") {
	  steps {
	    echo "${params.Greeting} Build World!"
      }
	}

    stage("test") {
	  steps {
	    echo "${params.Greeting} Test World!"
	  }
	}

    stage("deploy") {
	  steps {
	    echo "${params.Greeting} Deploy World!" 
	  }
	}

  }
}
