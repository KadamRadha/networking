pipeline {
    agent any



   stages {
        stage('Compile') {
            steps {
                echo 'Compile'
                bat 'mvn compile'
            }
        }
       
        stage('Package') {
            steps {
                echo 'Package'
                bat 'mvn package'
            }
            post {
                
                success {
                          archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
                }



            }
        }
        stage('Depoly') {
            steps {
                echo 'Deploy'
            withEnv(['JENKINS_NODE_COOKIE=dontKillMe']){
               bat 'start/min java -jar target/SocialNetwork-Backend-0.0.1-SNAPSHOT.war'
                }



           }
        }



   }
}

