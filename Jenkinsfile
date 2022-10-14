pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f java-tomcat-sample/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy dockerized version'){
            steps{
                sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"

            }
            
        }        
    }
 }

