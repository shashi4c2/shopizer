 node('ubuntu') {
    stage('GIT') {
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
