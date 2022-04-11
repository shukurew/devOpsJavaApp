
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
                            withCredentials([usernamePassword(credentialsId:'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]){
                            sh 'docker build -t shukurdocker/my-repo:jma-1.6 .'
                                sh "echo ${PASS} | docker login -u ${USER} --password-stdin"
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
