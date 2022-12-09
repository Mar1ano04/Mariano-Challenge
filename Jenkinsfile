
pipeline{
    agent {
        label 'worker-qa'
    }
    stages{
        stage("compile"){
            steps{
                sh 'mvn -DskipTests clean install package'
            }
        }
        stage("test"){
            steps{
                sh 'mvn test'
            }
        }
        stage("build-docker-image"){
            steps{
                sh 'docker image build -t spring-webapp .'
            }
        }
        stage("tag-docker-image"){
            steps{
                sh 'docker image tag spring-webapp mariano04/spring-webapp:latest'
            }
        }
        stage("upload-docker"){
            steps{
                sh 'docker login -u mariano04 -p dckr_pat_35EKsV8hUI9PPINaC2JuazKxVh0'
                sh 'docker image push mariano04/spring-webapp:latest'
            }
        stage("call-staging"){
            steps{
                build job: 'Staging-pipeline'
            }
        }
    }
}
