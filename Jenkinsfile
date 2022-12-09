pipeline{
    agent {
        label 'worker-staging'
    }
    stages{
        stage("pull-docker-image"){
            steps{
                sh 'docker pull mariano04/spring-webapp:latest'
            }
        }
        stage("retag-docker-image"){
            steps{
                sh 'docker image tag spring-webapp mariano04/spring-webapp:latest'
            }
        }
        stage("upload-docker"){
            steps{
                sh 'docker login -u mariano04 -p dckr_pat_35EKsV8hUI9PPINaC2JuazKxVh0'
                sh 'docker image push mariano04/spring-webapp:latest'
            }
        }
    }
}
