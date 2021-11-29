pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    
     stage('scm') {
            steps {
                git branch: 'master', credentialsId: '5e23c881-a453-43af-8083-6e4b12861e9d', url: 'https://github.com/nagarajshobha/pipeline.git'
            }
        }
         stage('build') {
            steps {
                bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
         stage('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '9c03d772-d4ed-4c1d-96be-1e44e134f178', path: '', url: 'http://localhost:8081/')], contextPath: 'myapp.war', war: '**/*.war'
            }
     }   }
}


