pipeline {
    agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh '''
                mvn test
                ls
                ''' 
            }
            post {
                always {
                    
                    junit allowEmptyResults: true, testResults: '**/surefire-reports/*.xml'

                    ///junit '**target/surefire-reports/*.xml'
 
                }
            }
        }
    }
}
