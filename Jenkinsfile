pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'mvn test'
            }
        }

        stage('Deploy to Cloudhub') {
            environment {
                ANYPOINT_CREDENTIALS = credentials('anypointplatform1')
            }
            steps {
                echo 'Deploying to CloudHub...'
                bat """
                   mvn mule:deploy \
                   -DmuleDeploy=true \
                   -DmuleVersion=4.9.0 \
                   -Dusername=selam-august \
                   -Dpassword=Selamet@123 \
                   -DworkerType=Micro \
                   -Dworkers=1 \
                   -Dregion=us-east-1
                """
            }
        }
    }
}
