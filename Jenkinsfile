#!/usr/bin/env groovy

library identifier: 'jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
         remote: 'https://github.com/ManideepM777/jenkins-shared-library.git',
         credentialsId: 'gitlab-access'
        ]
)

def gv

pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    buildJar()                  
                }
            }
        }
        stage("build and push image") {
            steps {
                script {
                    buildImage 'manideepm777/demo-app:4.0'
                    dockerLogin()
                    dockerPush 'manideepm777/demo-app:4.0'
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    gv.deployApp()
                }
            }
        }
    }   
}
