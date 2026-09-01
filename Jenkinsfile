#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('build app') {
            steps {
                script {
                    echo "building the application..."
                }
            }
        }
        stage('build image') {
            steps {
                script {
                    echo "building the docker image..."
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                    echo 'deploying docker image...'
                    withKubeConfig([credentialsId: 'lke-credentials', serverUrl: 'https://06a60f3f-c840-426c-b9bd-c6b420b0833e.in-maa-1-gw.linodelke.net']) {
                            sh 'kubectl create deployment nginx-deployment --image=nginx'
                    }
                }
            }
        }
    }
}