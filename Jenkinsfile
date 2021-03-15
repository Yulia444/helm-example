pipeline {
    environment {
        token = "eyJhbGciOiJSUzI1NiIsImtpZCI6IlRtMExiczNLXzhQTmN3akd0TUV3THZva3hfeGNfN2RLUU9yR3N6N2o1TzAifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImRlZmF1bHQtdG9rZW4tODk1OWMiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiZGVmYXVsdCIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6IjRjZWEzNmE2LTkyZDAtNDA1NC1hM2RmLWQ5NjU0Nzg2N2U5NCIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmRlZmF1bHQifQ.mPLCrJdrLm-OesFCSv2jz4f7cYSKNgPcbbN1qopGlKL1iJNOH8XmymaCzO2Xs6EnbjtdfWbQ5CEZsV2sa9KPql2A7Jbsy-5Q6oSCDP-rAEIDddWumS02oqpwSusmEK68Zo7uHPvZx-FBtZLlyT9jaM2-xrckQAhkaz-85dJOAsEPEwndh88YQDgtHM3S1xdRGTJ8GFjTImEP8MF5_C8eDYqQEVUA6vFyxzDOXq1ROPkJSGtC1EWBZxh7aqJcE19MoGaDHhoOo9lYhUNN5j8ApktOVoII-y_tD4tL36SDQHkMeXKIywy7Bir1s0X2iulmkypPi0dxqjYnFpadxjGMyQ"
    }
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
                sh "kubectl --kubeconfig=./config apply -f stepik-teachers/templates/deployment.yaml"
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