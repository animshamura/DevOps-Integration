pipeline {
    agent any
    tools{
        maven 'maven_3_5_0'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/animshamura/DevOps-Integration']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t animshamura/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   
                   sh 'docker login -u animshamura -p getsetit1

                   sh 'docker push animshamura/devops-integration'
                }
            }
        }

    }
}
