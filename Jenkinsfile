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

        stage('Deloy') {
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                    script {
                        waitUntil {
                            def ret = sh script: 'docker exec java-jdk java -jar /home/demojenkins-0.0.1-SNAPSHOT.jar', returnStdout: true
                            if (ret.trim() != "0" ) {
                                return false
                            } else {
                                return true
                            }                            
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
