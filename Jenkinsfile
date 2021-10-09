pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                     echo "this is tomy build step"
                     sh 'mvn -f hello-app/pom.xml -B -DskipTests clean package'
            }
            
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.jar'
                }
            }
        }        
        stage('Test') {
            steps {
                echo "Test stage is rınning."
                sh 'mvn -f hello-app/pom.xml test'
            }
            post {
                always {

                    junit 'hello-app/target/surefire-reports/*.xml'
                    
                }
            }
        }
    }
}
