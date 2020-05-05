pipeline {

    agent any

    stages {

    
                     
     

        stage ('Artifactory configuration') {

            steps {

                rtServer (

                    id: "ARTIFACTORY_SERVER1",

                    url: "https://sakthishivani.jfrog.io/artifactory",

                    credentialsId: 'jfrog'
                //    username: 'admin',
 //   password: 'A@runa11''

                )



                rtMavenDeployer (

                    id: "MAVEN_DEPLOYER",

                    serverId: "ARTIFACTORY_SERVER1",

                    releaseRepo: "libs-release-local",

                    snapshotRepo: "libs-snapshot-local"

                )



                rtMavenResolver (

                    id: "MAVEN_RESOLVER",

                    serverId: "ARTIFACTORY_SERVER1",

                    releaseRepo: "libs-release",

                    snapshotRepo: "libs-snapshot"

                )

            }

        }

        stage('package') {
            steps {
                rtMavenRun (
                    tool: 'maven',
                     pom: 'pom.xml',
                    goals: 'clean install package',
                    deployerId: "MAVEN_DEPLOYER",
                    resolverId: "MAVEN_RESOLVER"
                    )
            }
        }
        
     
       

       

        
         stage('deploy') {
        steps {
            
           sh 'cp target/JPetStore.war /home/dineshreddy99077/noida/apache-tomcat-7.0.103/webapps/'
        }
        }



     

    }

}
