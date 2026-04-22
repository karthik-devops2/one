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
            pwd
            ls -R
            FILE=$(ls target/*.war | head -n 1)
            echo "WAR file is: $FILE"

            curl -u tomcat:admin@123 \
                 --upload-file "$FILE" \
                 "http://13.54.11.128:8080/manager/text/deploy?path=/myweb&update=true"
        '''
    }
}
    }
}
