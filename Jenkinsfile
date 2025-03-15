pipeline{
    agent any
    tools{
        maven "MAVEN3.9"
        jdk "JDK11"
    }
    stages{
        stage('fetch code'){
            git branch: 'main', url: 'https://github.com/k1d1r2m/tomcat.git'
        }

        stage('Build'){
            sh 'mvn clean packages'
        }

        stage('copy file to remote server'){
            sh 'scp -i **/*.war root@192.168.0.110:/root/tomcat/webapps'
        }

        stage('go to bin dir'){
            sh '/root/tomcat/bin/startup.sh'
        }
    }
}
