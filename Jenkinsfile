pipeline {
    agent ("ubuntu") { 
        stage('GIT') {
            git credentialsId: '4de9f9d4-0f20-4393-87b2-c775c03a59f5',
            git 'https://github.com/shashi4c2/shopizer.git'
            }
        stage('package') {
            sh 'mvn package'
            }
        stage('archiveartifacts') {
            archive 'shopizer-shop/target/*.jar'
            }
        stage('archivetestresults') {
            junit 'shopizer-shop/target/surefire-reports/*.xml'
           }
    }
}
