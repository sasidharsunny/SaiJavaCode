pipeline {
    agent any
      tools {
        maven 'MAVEN3'
    }
    environment{
        ARTIFACTORY_SERVER = "Artifactory"
        ARTIFACTORY_REPO = "maven-artifact"
    }

   stages {
        stage('Git clone') {
            steps {
     git 'https://github.com/sasidharsunny/SaiJavaCode.git'
}
        }
        
   stage('Build') {
            steps {
     sh "mvn clean install"
    }
    }
       
  
       


 

}
}
