
pipeline {
    agent any
    tools{
    maven 'maven_3.6'
    }
    stages {

        stage("build jar") {
            steps {
                script {
                    echo "building the application"
                    sh 'mvn package'

                }
            }
        }


         stage("building image") {
                    steps {
                        script {
                            echo "building the image ..."
                            withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                            sh 'docker build -t shukurdocker/my-repo:jma-1.6 .'
                            sh "docker login -u $USERNAME -p $PASSWORD"
                            sh 'docker push shukurdocker/my-repo:jma-1.6'


                            }


                        }
                    }
                }




        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                }
            }
        }


    }   
}
