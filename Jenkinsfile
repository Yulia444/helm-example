pipeline {

    agent any
    stages {
        stage("Installing helm ") {
            steps {
                sh(
                    label: "Installing helm",
                    script: """#!/usr/bin/env bash
                    tar -xvzf helm-v3.5.3-linux-arm64.tar.gz
                    mv linux-arm64/helm helm"""
                    
                )
            }
        }
        stage("kubectl") {
            steps {
                script {
                    withKubeConfig(credentialsId: "kubesecret") {
                        sh 'kubectl apply -f stepik-teachers/templates/deployment.yaml'
                    }
                }
            }
        }
        stage("Deploy pods") {
            steps {
                sh(
                    label: "Deploy pods",
                    script: """#!/usr/bin/env bash
                    helm install stepik-teachers stepik-teachers"""
                )
            }
        }
    }
}