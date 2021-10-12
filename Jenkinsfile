pipeline{
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven-3.6.0"
      }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/ravdy/javaloginapp.git'
            }
         }        
       stage('Build'){
            steps{
                //sh 'mvn clean package'
                bat "mvn clean package"
            }
         }
        stage('SonarQube analysis') {
            def scannerHome = tool 'scanner';
            steps{
                withSonarQubeEnv('sonar') { 
                    // If you have configured more than one global server connection, you can specify its name
                    //      sh "${scannerHome}/bin/sonar-scanner"
                    //sh "mvn sonar:sonar"
                    bat "${scannerHome}/sonar-scanner"
                    bat "mvn sonar:sonar"
                }
            }
        } 
    }
}
