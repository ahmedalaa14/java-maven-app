#!/usr/bin/env groovy

library identifier: 'jenkins-shared-library@master', retriever: modernSCM(
        [$class: 'GitSCMSource',
         remote: 'https://github.com/ahmedalaa14/jenkins-shared-library.git',
         credentialsId: 'Github-Credential'
        ]
)


def gv

pipeline {
    agent any
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
                    buildImage 'ahmedalaa14/demo-app:jma-2.0'
                    dockerLogin()
                    dockerPush 'ahmedalaa14/demo-app:jma-2.0'
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                }
            }
        }
    }   
}
