pipeline {
    agent any

    stages {
        stage ('Deloy') {
            steps {
                timeout(5) {
                    waitUntil {
                        script {
                        def r = sh script: 'docker exec java-jdk java -jar /home/demojenkins-0.0.1-SNAPSHOT.jar sleep 90', returnStatus: true
                        return (r == 0);
                        }
                    }
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
