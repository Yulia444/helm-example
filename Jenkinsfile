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
                        sh 'kubectl --token=eyJhbGciOiJSUzI1NiIsImtpZCI6IlRtMExiczNLXzhQTmN3akd0TUV3THZva3hfeGNfN2RLUU9yR3N6N2o1TzAifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImplbmtpbnMtdG9rZW4taDd6eGoiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiamVua2lucyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6IjdmMmI2MDI3LTcyOWItNGI0MS04OTUzLWE5YzRiYzYwZGM1NSIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmplbmtpbnMifQ.Doga7nEgOlADhlZLXdUFCaBIP_T1Tk-UjNfZVIOCE6BwSIn0BAsBJTELvujyXQzOQue3Z3_fbveDRAjFCHdObWBbs_QMzCBjaqXuc1zVa0_Ldo_RvDVGb90DWXVXp_L9_2xM4ZANQLePCMJexh1zsyYuqdGA35aJ8QOIv5qlVgPCuO3V0pMeI5RfjmkfebFQFny_PJjDrogf3a0o2VOzwQSsHLWHFyUIbbmXKbgtGClUPpHWHU4c-amKrGrg3sBDhY7Q3lVS90NdYpQh5C8y_qIFPNAPOEzRgeaDt6EmvnYxf8q_ppVqjVofM0jSIlcuYDCK0cGXlznOt6xxb8hkYA apply -f stepik-teachers/templates/deployment.yaml'
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