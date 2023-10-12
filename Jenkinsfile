pipeline {
    agent any
    tools{
        maven 'Maven_3_9_4'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'test2_process', url: 'https://github.com/vinoshanvlr/spring-demo']])
                bat 'mvn clean install'
            }
        }
          stage('Build docker image'){
            steps{
                script{
                    bat 'docker build . -t vinoshan/devops-integration'
                }
            }
        }
         stage('Push image to Hub'){
            steps{
                script{
                  
                    bat 'docker login -u vinoshan -p Vinoshan@123'

                    bat 'docker push vinoshan/devops-integration'
                }
            }
        }
    }
}
    
    