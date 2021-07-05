pipeline {
    agent any
    
    environment {
        DOCKER_USER = 'tho861998'
        DOCKER_REGISTRY = 'docker.io'
    }

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', credentialsId: '56164834-c6ef-47bd-9673-2085a65ec92e', url: 'http://localhost/thaunghtikeoo/catgif.git'
            }
        }
        stage('docker image building') {
            steps {
                sh 'docker build -t tho861998/cat:1.${BUILD_NUMBER} .'
            }
        }
        stage('docker login') {
            steps {
                sh 'docker login -u $DOCKER_USER -p $DOCKER_PASSWORD $DOCKER_REGISTRY'    
            }
        }
        stage('docker push') {
            steps {
                sh 'docker push tho861998/cat:1.${BUILD_NUMBER}'
            }
        }
        stage('Deploy App') {
            steps {
                kubeconfig(caCertificate: 'LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUREekNDQWZlZ0F3SUJBZ0lVVjBwK2F1angyUmZLdWg2U0hLbFNxMkZKazJvd0RRWUpLb1pJaHZjTkFRRUwKQlFBd0Z6RVZNQk1HQTFVRUF3d01NVEF1TVRVeUxqRTRNeTR4TUI0WERUSXhNRGN3TkRFME1EUXdOMW9YRFRNeApNRGN3TWpFME1EUXdOMW93RnpFVk1CTUdBMVVFQXd3TU1UQXVNVFV5TGpFNE15NHhNSUlCSWpBTkJna3Foa2lHCjl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUE1cjdGTkVoVzE3R3c2NlJiUnNOK2Zxdk9CZjloQ3RsNXlGdzAKRVJHc2k5dVZOZ3R6TS9KQlVGZkJXRC9BdGJjaCtOL0NIRnV2UVlaZU9JZVFKb1FUVG0wNU15b0ZCQ0pSS3lUaAozaUw2bHNFdUtSbU1FVEtaZFg3RjI0Mk5iTm5rVEUzU1V5YzdBMzNORStxNXk0TXdxK3dGb1VFRW41eEM5ODMvClRHY05ub2F2cm9HeWxKM1FDbVhLWlp3VEZhb2RuWWFHUmQ2aHo2TUVtTHdQalJrQWFib29jMEoyMTJkbG5TTG0KSzJuRTh2aHN1c1djWFByTCtlbHd2UzdmMFZBOUF6YmMzbzB6RzEzMUxyWS8vTGV5Z2l6Uy92Ty82S2FoSjl6dQpmU1NCM29zRVlORWNxNTl2bktyQlJEUUxkN2lEY1JVNExYTVJ0RVludk1JSndKZlNad0lEQVFBQm8xTXdVVEFkCkJnTlZIUTRFRmdRVVhaeWQzWXM1UVMyR3NkdDNrV0w2bCtweVRxSXdId1lEVlIwakJCZ3dGb0FVWFp5ZDNZczUKUVMyR3NkdDNrV0w2bCtweVRxSXdEd1lEVlIwVEFRSC9CQVV3QXdFQi96QU5CZ2txaGtpRzl3MEJBUXNGQUFPQwpBUUVBQ2hOZkdjRU1kN3JveHRHT0c3R1RhQStXNWROQjB6VjhWcit5T0FCenNxNjNlZ0E2UEdNdmtJRVdDaTBpCjlOR2dSQ3lQMFZHdHNDNWlmWXpGaFRPMGo5eWhkY240MzRmcDNTR0VCU2ZmZDIwV3hkV3BQQURYcG5tUW1WK2UKRDluWDJ2Wmh1L0kyaHRsYWo1V1podHlEL3dzci9zTE1KY1RjNU9HMEJWVWlwV1h2bXA5MHBOUkt4U01qeHRtbgpqczdEeGtUaVlRaHR5TWpvMTZ4Zk9DY0ZXNC8rWEI4TXVtNit1aklycENNd2YzaGlVcjVheGpGNGYrOTFSaWF5CnBjYjdVTWZseE5kSHhFdkJJL3N0SEhWb25CeWFhMUtUTG9aZHh5QXlEc1MrQ3ZMcXpzdWZheEdJenE0RnI5TEgKNXZhRjJyK25JMFIxQ24xWW9DSUUyTDl3RGc9PQotLS0tLUVORCBDRVJUSUZJQ0FURS0tLS0tCg==', credentialsId: 'thok8sconfig', serverUrl: 'https://127.0.0.1:16443') {
                script {
                    sh 'kubectl get nodes'
                    sh 'ls'  ##list files from git repo
                    sh 'ls /home/thaunghtikeoo'
                    sh 'kubectl apply -f cat.yaml' ## cat.yaml from git repo ( not your local machine )
                    }
                }    
            }
        }
    }
}
