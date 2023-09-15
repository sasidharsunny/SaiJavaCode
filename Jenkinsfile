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
    sh 'mvn clean package'
    }
    }
       
  
       
    stage('Upload to Artifactory') {
            steps {
                script {
                    def server = Artifactory.server('Artifactory')
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "*.war",
                                "target": "maven-artifact/"
                            },
                              {
                                "pattern": "*.jar",
                                "target": "maven-artifact/"
                            },
                             {
                                "pattern": "*.pom.xml",
                                "target": "maven-artifact/"
                            }
                        ]
                    }"""
                    server.upload(uploadSpec)
                }
            }
        }  

 

}
}

