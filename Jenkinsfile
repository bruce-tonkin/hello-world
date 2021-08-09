pipeline {
agent any
  parameters {
    string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    string(name: 'SDLC', defaultValue: 'Delivery', description: 'What environment should this be run against?')
  }

  switch (ENV) {
    case "Delivery":
      echo 'Building Delivery';
      env.SDLC = 'delivery';
      break;
    case "Test":
      echo 'Building Test';
      env.SDLC = 'test';
      break;
    case "Production":
      echo 'Building Production';
      env.SDLC = 'production';
      break;
    default:
      echo 'Nothing selected';
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
