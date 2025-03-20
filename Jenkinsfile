pipeline {
    agent any
    tools {
        maven 'DHT_MVN'
        jdk 'DHT_SENSE'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/wesleykim2002/maven-samples-A6.git', branch: 'master'
            }
        }
        stage('Run Git Bisect') {
            steps {
                sh '''
                git bisect start
                git bisect bad 198644632661c67b6c32f59e9047c11a70685e15
                git bisect good 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5
                git bisect run mvn clean test
                git bisect reset
                '''
            }
        }
    }
}
