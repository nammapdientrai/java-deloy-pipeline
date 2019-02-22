pipeline {
    agent any

    stages {
        stage ('Deloy') {
            steps {
                sh 'docker exec java-jdk java -jar /home/demojenkins-0.0.1-SNAPSHOT.jar'  
            }

            post {
                always {
                    echo 'running .......'
                }
            }
        }

        stage('Success') {
            steps {
                echo 'Success....'
            }
        }
    }
}
