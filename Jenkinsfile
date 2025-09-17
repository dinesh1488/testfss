@Library('dc2-lib')_

pipeline {
agent { label 'DockerIO-3' }


        stages {
                stage('Initialise') {
                steps {
                        init()
                        }
                }
                stage('Helm Lint ') {
                steps {
                        helmLint()
                        }
                }
                stage('Docker Image Push ') {
                steps {
                        pushITVSDPDockerImages()
                        }
                }


                stage('Helm Test ') {
                steps {
                        helmTest()
                        }
                }

                stage('Helm Package & Publish ') {
                steps {
                        helmPackage()
                        }
                }
        stage ('Deploy to Openshift') {
        steps {
            deploytoOpenshift()
            }
        }
                stage ('Notify') {
        steps {
            sendNotification()
            }
        }
        }
}
