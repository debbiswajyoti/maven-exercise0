pipeline{
    agent{
        node{ label 'docker-agent' }
    }
    tools{
        maven 'apache-maven-3.3.1'
    }
    options{
        buildDiscarder(logRotator(numToKeepStr: '2'))
        disableConcurrentBuilds()
        disableResume()
        timestamps()
    }
    stages{
        //stage('get repo'){
        //    steps{
        //        sh '''
        //            echo "cloning project from gitHub"
        //        '''
        //        checkout([$class: 'GitSCM', branches:[[name:'*/main']], userRemoteConfigs:[[CredentialsId:'debbiswajyoti_git', url:'https://github.com/debbiswajyoti/maven-exercise0.git']]])
        //    }
        //}
        stage('check content'){
            steps{
                sh 'pwd'
                sh 'ls -ltr'
            }
        }
        stage('maven complie'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: 'target/myApp-1.0-SNAPSHOT.jar', fingerprint: true, allowEmptyArchive: false, onlyIfSuccessful: false;
        }
        cleanup{
            cleanWs()
        }
    }
}
