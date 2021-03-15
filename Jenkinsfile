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
                    withKubeCredentials([[credentialsId: "kubesecret"]]) {
                        sh '''kubectl --token=ZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklsUnRNRXhpY3pOTFh6aFFUbU4zYWtkMFRVVjNUSFp2YTNoZmVHTmZOMlJMVVU5eVIzTjZOMm8xVHpBaWZRLmV5SnBjM01pT2lKcmRXSmxjbTVsZEdWekwzTmxjblpwWTJWaFkyTnZkVzUwSWl3aWEzVmlaWEp1WlhSbGN5NXBieTl6WlhKMmFXTmxZV05qYjNWdWRDOXVZVzFsYzNCaFkyVWlPaUprWldaaGRXeDBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5elpXTnlaWFF1Ym1GdFpTSTZJbXBsYm10cGJuTXRkRzlyWlc0dGFEZDZlR29pTENKcmRXSmxjbTVsZEdWekxtbHZMM05sY25acFkyVmhZMk52ZFc1MEwzTmxjblpwWTJVdFlXTmpiM1Z1ZEM1dVlXMWxJam9pYW1WdWEybHVjeUlzSW10MVltVnlibVYwWlhNdWFXOHZjMlZ5ZG1salpXRmpZMjkxYm5RdmMyVnlkbWxqWlMxaFkyTnZkVzUwTG5WcFpDSTZJamRtTW1JMk1ESTNMVGN5T1dJdE5HSTBNUzA0T1RVekxXRTVZelJpWXpZd1pHTTFOU0lzSW5OMVlpSTZJbk41YzNSbGJUcHpaWEoyYVdObFlXTmpiM1Z1ZERwa1pXWmhkV3gwT21wbGJtdHBibk1pZlEuRG9nYTduRWdPbEFEaGxaTFhkVUZDYUJJUF9UMVRrLVVqTmZaVklPQ0U2QndTSW4wQkFzQkpURUx2dWp5WFF6T1F1ZTNaM19mYnZlRFJBakZDSGRPYldCYnNfUU16Q0JqYXFYdWMxelZhMF9MZG9fUnZEVkdiOTBEV1hWWHBfTDlfMnhNNFpBTlFMZVBDTUpleGgxenN5WXVxZEdBMzVhSjhRT0l2NXFsVmdQQ3VPM1YwcE1lSTVSZmpta2ZlYkZRRm55X1BKakRyb2dmM2EwbzJWT3p3UVNzSExXSEZ5VUliYm1YS2JndEdDbFVQcEhXSFU0Yy1hbUtyR3JnM3NCRGhZN1EzbFZTOTBOZFlwUWg1Qzh5X3FJRlBOQVBPRXpSZ2VhRHQ2RW12bll4ZjhxX3BwVnFqVm9mTTBqU0lsY3VZRENLMGNHWGx6bk90Nnh4Yjhoa1lB apply -f stepik-teachers/templates/deployment.yaml'''
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