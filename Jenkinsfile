#!/usr/bin/env groovy

pipeline {
  agent {
    kubernetes {
      label 'kube-test'
      defaultContainer 'jnlp'
      yamlFile 'KubernetesPod.yaml'
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
        container('busybox') {
          sh '/bin/busybox'
        }
      }
    }
  }
}
