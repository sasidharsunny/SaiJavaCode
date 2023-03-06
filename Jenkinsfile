pipeline {
    agent any
    environment{
        PATH = "/opt/apache-maven-3.6.3/bin/:$PATH"
        ARTIFACTORY_SERVER = "jfrog-server-2"
        ARTIFACTORY_REPO = "maven"
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
    stage('Upload to Artifactory') {
            steps {
                script {
                    def server = Artifactory.server('jfrog-server-2')
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "*.war",
                                "target": "maven/"
                            },
                              {
                                "pattern": "*.jar",
                                "target": "maven/"
                            },
                             {
                                "pattern": "*.pom.xml",
                                "target": "maven/"
                            }
                        ]
                    }"""
                    server.upload(uploadSpec)
                }
            }
        }  

 

}
}

