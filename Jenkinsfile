//START-OF-SCRIPT
//node {
//    def SONARQUBE_HOSTNAME = '34.214.185.4'
//    def RELEASENAME = "webapp-1.0.war"

//    def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
 //   def GRADLE_HOME = "/opt/gradle/gradle-4.10.2"
 //   sh "${GRADLE_HOME}/bin/gradle tasks"

   // stage('Clone') {
   //      git url: 'https://github.com/HugoAquinoNavarrete/devops-webapp3.git'
   // }

   // stage('build') {
    //    sh "${GRADLE_HOME}/bin/gradle build -PwarName=${RELEASENAME} --info"
   // }

//}
//END-OF-SCRIPT

pipeline {
  environment {
     def sonarqubeScannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
  }

  agent any

  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/HugoAquinoNavarrete/devops-webapp3', branch: 'main')
      }
    }

    stage('Build') {
      steps {
        sh '''/opt/gradle/gradle-4.10.2/bin/gradle tasks
        /opt/gradle/gradle-4.10.2/bin/gradle build -PwarName=${RELEASENAME} --info   
           '''
      }
    }

    stage('sonar-scanner') {
//      def sonarqubeScannerHome = tool name: 'sonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      steps {
          withSonarQubeEnv('sonarqube') {
//        withCredentials([string(credentialsId: 'sonar', variable: 'sonarLogin')]) {
        sh '''${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://34.214.185.4:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=WebApp - Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=GS -Dsonar.sources=java-demo-app/src/main/ -Dsonar.tests=java-demo-app/src/test/ -Dsonar.language=java
           '''
        }
      }
    }



  }
}
