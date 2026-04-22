pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
           steps {
             sh '''
               FILE=$(ls myDeployment/target/*.war)
               echo "Deploying $FILE"

               curl -u tomcat:admin@123 \
               --upload-file $FILE \
               "http://13.54.11.128:8080/manager/text/deploy?path=/myapp&update=true"
             '''
    }
}
    }
}
