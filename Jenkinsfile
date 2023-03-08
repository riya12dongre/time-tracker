pipeline{
    agent any
    tools{
        maven 'MAVEN'
 }
    stage{
        stage('Build'){
             steps{
                 bat 'mvn clean packge'
             }
             post{
                 success{
                    echo" Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                 }
             }
         }
         stage (''){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'c3121423-9a47-42dd-a560-98da8d7e4605', path: '', url: 'http://localhost:8090')], contextPath: null, war: '**/*.war'
            }
       }
    }
}
