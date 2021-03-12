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
        stage("Deploy pods") {
            steps {
                sh(
                    label: "Deploy pods",
                    script: """helm install stepik-teachers stepik-teachers"""
                )
            }
        }
    }
}