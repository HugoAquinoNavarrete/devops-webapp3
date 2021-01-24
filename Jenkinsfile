//START-OF-SCRIPT
node {
    def SONARQUBE_HOSTNAME = '34.214.185.4'

//    def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
    def GRADLE_HOME = "/opt/gradle/gradle-4.10.2"
    sh "${GRADLE_HOME}/bin/gradle tasks"

    stage('Clone') {
          sh "pwd"
         git url: 'https://github.com/HugoAquinoNavarrete/devops-webapp3.git'
    }

    stage('build') {
        sh "${GRADLE_HOME}/bin/gradle build"
    }



}
//END-OF-SCRIPT
