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




  }
}
