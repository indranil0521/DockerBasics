pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn clean package'
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

