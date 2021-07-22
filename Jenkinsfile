pipeline {
    environment {
        DockerhubUri = 'https://index.docker.io/v1/'
        DockerhubCred = 'Dockerhub'
        DockerhubBuildTag = 'pwang009/voting-app:latest'
        KubeDir = '/var/lib/jenkins'
        branch = "${GIT_BRANCH.substring(7)}"
    }
    agent any
    stages {
    /*
        stage('Build and Push Image') {
            steps {
                script {
                    dir("$WORKSPACE/voting-app") {
                        image = docker.build DockerhubBuildTag 
                        docker.withRegistry( '', DockerhubCred ) { image.push() }
                    }
                }
            }
        }
        */
        stage('Deploy to Kubernetes') {
            steps {
                dir("$WORKSPACE") {
                sh """
                    #!/bin/bash
                    echo $USER
                    echo $branch
                    echo "Starting deployment"
                    ## export KUBECONFIG=$KubeDir/.kube/local:$KubeDir/.kube/mini
                    ## /usr/local/bin/kubectl config use-context mini@kubernetes 
                    ## /usr/local/bin/kubectl delete -f ./voting-app-redis-k8s.yaml
                    ## /usr/local/bin/kubectl apply -f ./voting-app-redis-k8s.yaml 
                    ## /usr/local/bin/helm uninstall voting-app 
                    ## /usr/local/bin/helm install voting-app ./helm  -f "./helm/mini.values.yaml"
                   """
                }
            }
        }
    }
}
