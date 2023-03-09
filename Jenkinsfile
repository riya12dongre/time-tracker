pipeline{
    agent any
    tools{
        maven 'MAVEN'
 }
    stages{
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
         stage ('Deploy to tomcat server'){
            steps{
             deploy adapters: [tomcat9(credentialsId: '2ba90576-10dc-43fb-a386-cb99ac130afe', path: '', url: 'https://localhost:8090')], contextPath: null, war: '**/*.war'            }
       }
    }
}
