pipeline {
    agent any
    tools{
        maven 'MAVEN'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'a1cc2e05-ab66-4b9d-8b97-3811a1d663ba', url: 'https://github.com/mareh786/simple-java-maven-app.git']])
                sh 'mvn -Dmaven.test.failure.ignore=true clean package'
            }
        }
    }
    post{
        always{
            junit(
                allowEmptyResults:true,
                testResults:'*test-reports/.xml'
                )
        }
    }
}
