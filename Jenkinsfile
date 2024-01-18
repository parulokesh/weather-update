pipeline {
    agent { label 'slave4' }
    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf weather-update'
                sh 'git clone https://github.com/parulokesh/weather-update.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
          sh 'ssh root@172.31.14.255'
                sh 'scp /home/slave4/workspace/weather-update_Develop/target/weather-forecast-app-1.0-SNAPSHOT.jar root@172.31.14.255:/opt/apache-tomcat-8.5.98/webapps'
        }
        }
    } 
} 
