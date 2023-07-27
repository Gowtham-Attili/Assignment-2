pipeline {
    agent any



    tools {
        maven "Maven"
    }



    stages {
        stage('Clean') {
            steps {
                git 'https://github.com/Gowtham-Attili/nhg.git'
                 bat "mvn clean"
            }


            post {
                success {
                    echo 'Cleaning Project is Done'
                }
            }
        }



        stage('Compile') {
            steps {
                git 'https://github.com/Gowtham-Attili/nhg.git'
                 bat "mvn compile"
            }

            post {
                success {
                   echo 'Compiling Project is Done'
                }
            }
        }



        stage('Test') {
            steps {
                git 'https://github.com/Gowtham-Attili/nhg.git'
                 bat "mvn -Dmaven.test.failure.ignore=true test"
            }



            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'

                }
            }
        }





stage('Package') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Pprashu-63/Maven.git'





                // To run Maven on a Windows agent, use
                 bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }



            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                 archiveArtifacts 'target/*.jar'
                }
            }
        }



    }
}