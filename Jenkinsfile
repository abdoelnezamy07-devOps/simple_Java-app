pipeline{
    agent{
        label 'ec2-agent'
    }
    stages{
        stage('build'){
            steps{
                script{
                    sh 'docker build -t java-app .'
                }
            }
        }
        stage('Push'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'Password', usernameVariable: 'Username')]) {
                
                        sh 'docker login --username $Username --password $Password'
                        sh 'docker tag java-app $Username/java-app'
			sh 'docker push $Username/java-app'
                    }
                }
            }
        }
        stage('deploy'){
            steps{
                script{
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-cli', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                    
                        sh 'aws eks create --name pipe --region us-east-1'
                        sh 'kubectl apply -f ./k8s/deployment.yaml'
                    }
                }
            }
        }
    }
}
