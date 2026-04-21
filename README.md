pipeline
{
    agent any
    environment
{
        dockerimage=
        registry='4vv23ci064/test14'
        registryCredential='jenkin_docker_token'
}

stages

{

    stage('Checkout')
  
    {
        steps{
            checkout scmGit(branches:[[name:'*/main']],extensions:[],userRemoteConfigs:[[url:'https://github.com/Nithaksha-07/programiz.git']])
            
        }
        
    }
    stag('Build Docker Image')
    {
        steps{
            
            script{
                dockerimage=docker.build registry
            }
        }
    }
}
    }
}
