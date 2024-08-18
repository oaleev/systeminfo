pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Compiling the App'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'Running Unit tests'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'Packaging the app...'
        sh '''# Truncate the GIT_COMMIT to the first 7 Characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.6'
  }
  post {
    always {
      echo 'this maven pipeline has completed...'
    }

  }
}