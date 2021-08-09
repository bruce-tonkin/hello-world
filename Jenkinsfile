pipeline {
	agent {kurhah}
  parameters {
    string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
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
