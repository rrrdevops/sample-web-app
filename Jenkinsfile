pipeline {
    agent any
    
    tools {
        maven 'Maven 3.8.6'
        jdk 'openjdk-11'
    }
    stages {
        stage ('Code Checkout') {

            steps {
                  git branch: 'main', url: 'https://github.com/rrrdevops/sample-web-app.git'
                }
            }
        

        stage ('Build Stage') {

            steps {
              sh '''
              JAVA_HOME=/var/lib/jenkins/tools/hudson.model.JDK/openjdk-11/jdk-11.0.1
              mvn clean install
              '''
                }
            }
        


        stage ('Deploy Stage') {
            steps {
                 sudo scp  /var/lib/jenkins/workspace/web-freestyle/webapp/target/webapp.war root@172.31.40.241:/opt/tomcat/webapps/
                }
            }
        
    }
}
