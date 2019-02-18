#!/usr/bin/env groovy

pipeline {
    agent { node { label 'master' } }

    stages {
        stage('Build') {
            steps {
                sh './gradlew asciidoctor'
                archiveArtifacts artifacts: 'build/guides/html5/**'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '5'))
    }
}