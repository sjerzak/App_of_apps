def frontendImage="isirli/frontend"
def backendImage="isirli/backend"
def backendDockerTag=""
def frontendDockerTag=""
def dockerRegistry=""
def registryCredentials="dockerhub"

pipeline {
    agent {
        label 'agent'
    }

    stages {
        stage('Get Code') {
            steps {
                checkout scm
            }
        }
    
        stage('Adjust version') {
            steps {
                script{
                    backendDockerTag = params.backendDockerTag.isEmpty() ? "latest" : params.backendDockerTag
                    frontendDockerTag = params.frontendDockerTag.isEmpty() ? "latest" : params.frontendDockerTag
                    
                    currentBuild.description = "Backend: ${backendDockerTag}, Frontend: ${frontendDockerTag}"
                }
            }
        }

        stage('Clean running containers') {
            steps {
                sh "docker rm -f frontend backend"
            }
        }
    }



    parameters {
        string 'backendDockerTag'
        string 'frontendDockerTag'
    }
}