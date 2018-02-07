pipeline {
  agent {
    label 'master'
  }
  stages {
    stage('Example') {
      steps {
        echo 'Hello World'
        script {
          def browsers = ['chrome', 'firefox']
          for (int i = 0; i < browsers.size(); ++i) {
            echo "Testing the ${browsers[i]} browser"
            @Library('slack')
            import slack.Slack
            Slack slack = new Slack();
            slack.sendNotification('ok');

          }
        }
        
      }
    }
    stage('Example2') {
      parallel {
        stage('Example2') {
          steps {
            echo 'Example2 step '
          }
        }
        stage('Example3') {
          steps {
            sh 'echo "example 2 from docker"'
          }
        }
      }
    }
  }
}