#!/usr/bin/env groovy

pipeline {
  agent any

  environment {
    NEXUS_SONATYPE_PASSWORD = credentials('nexus-sonatype-password')
    NEXUS_ODE_PASSWORD = credentials('nexus-ode-password')
  }

  stages {
    stage('Build') {
      steps {
        checkout scm
        sh './build.sh clean install publish'
      }
    }
  }
  
  post {
    cleanup {
      sh 'docker-compose down'
    }
  }
}