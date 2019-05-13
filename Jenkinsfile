#!/bin/bash -l
#!/usr/bin/env groovy

pipeline {
  agent any
  tools {nodejs "latest"}
  stages {
    stage('Pre-checks') {
      steps {
        echo sh(returnStdout: true, script: 'env')
        sh 'node -v'
      }
    }
    stage('Build from Master') {
      steps {
        sh 'npm --version'
        sh 'git log --reverse -1'
        sh 'npm install'
      }
    }
    stage('Start Application') {
      steps {
        sh 'node .'
      }
    }
    stage('Start Test') {
      steps {
        sh 'npm test'
      }
    }
  }
}
