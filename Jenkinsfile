pipeline {
    environment {

    }
    agent: any
    stages{
        stage("Installing helm "){
            steps {
                sh(
                    label: "Installing helm",
                    script: """#!/usr/bin/env bash
                    tar -xvzf helm-v3.1.0-linux-amd64.tar.gz
                    mv linux-amd64/helm helm"""
                    
                )
            }
        }
        stage("Deploy pods"){
            steps{
                sh(
                    label: "Deploy pods",
                    script: """helm install stepik-teachers stepik-teachers"""
                )
            }
        }
    }
}