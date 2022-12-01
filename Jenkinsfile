pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
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
      steps {
            bat 'mvn clean deploy -Pdev -DmuleDeploy -Danypoint.username=sistech23 -Danypoint.password=11GrandTerrace -Danypoint.platform.client_id=cd3e7991816740848e94f42c034cb95d -Danypoint.platform.client_secret=31d65B7471184D6783c4Bb57e0F54218 -Denc.key=abcdef0123456789'
      }
    }
  }
}