pipeline {
    agent any
    environment{
        PATH = "/opt/apache-maven-3.6.3/bin/:$PATH"
        ARTIFACTORY_SERVER = "jfrog-server-1"
        ARTIFACTORY_REPO = "example-repo-local"
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
                    def server = Artifactory.server('jfrog-server-1')
                    def uploadSpec = """{
                        "files": [
                            {
                                "pattern": "*.war",
                                "target": "example-repo-local/"
                            },
                              {
                                "pattern": "*.jar",
                                "target": "example-repo-local/"
                            },
                             {
                                "pattern": "*.pom.xml",
                                "target": "example-repo-local/"
                            }
                        ]
                    }"""
                    server.upload(uploadSpec)
                }
            }
        }  

 

}
}

