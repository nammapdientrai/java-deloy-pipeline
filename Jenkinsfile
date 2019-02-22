pipeline {
    agent any

    stages {
        stage('Setup container JDK') {
            steps {
                sh 'docker container stop java-jdk'
                sh 'docker container rm java-jdk'
                sh 'docker run --name java-jdk -d -v /opt/tomcat/.jenkins/workspace/java-full-pipeline/demojenkins/target:/home -i openjdk'
            }
        }

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
