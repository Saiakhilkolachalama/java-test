pipeline {
    agent any

    environment {
        function_name = 'jenkins'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build'
                sh 'mvn package'
            }
        }
        stage('Push') {
            steps {
                echo 'Push'
                sh "aws s3 cp target/sample-1.0.3.jar s3://xxx7888"
            }
        }

        stage('Deploy') {
            steps {
                echo 'deploy'

                sh "aws lambda update-function-code --function-name $function_name --region us-east-1 --s3-bucket xxx7888 --s3-key sample-1.0.3.jar"
            }
        }
    }
}
