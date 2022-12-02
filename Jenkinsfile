pipeline {
  agent any
  environment {
    //Anypoint Platform Credentials 
    ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
    //Encryption key
    ENC_KEY = credentials('ENCRYPTION_KEY')
  }
  stages {
    stage('Build') {
      steps {
      		echo '***Build has started***'
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
      	  echo "****Munit test is in progress...***"
      	  bat 'mvn test'
      }
    }

     stage('Deployment') {
       environment {
    //DEV environment Specific credentials
    	CLIENT_ID = credentials('DEV_CLIENT_ID')
    	CLIENT_SECRET = credentials('DEV_CLIENT_SECRET')
  }
      steps {
      		echo '***Deployment has begun***'
            bat 'mvn clean deploy -Pdev -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%" -Denc.key="%ENC_KEY%"'
      }
    }
  }
}