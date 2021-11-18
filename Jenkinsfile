pipeline {
    agent none
    stages {
        stage('GIT')
            {
            agent {
                label 'ubuntu'
            }
            steps {
            git credentialsId: '4de9f9d4-0f20-4393-87b2-c775c03a59f5',
			url: 'https://github.com/shashi4c2/shopizer.git'
            }
        }   
		stage('Build from Maven ROOT')
			{
			agent { 
                label 'ubuntu'
            }
			steps {
			echo "building root POM from maven project"
			sh 'mvn clean install'
			}	
		}
		stage('Archieve Artifacts')
		    {
		    agent {
		         label 'ubuntu'
            }
		    steps {
		    echo "Artifacts"
		    archiveArtifacts 'sm-shop/target/*.jar, sm-shop/target/*.war'
		    }
		}
		stage('Test Results')
		    {
		    agent {
		        label 'ubuntu'
		    }
		    steps {
		    echo "Test Results"
		    junit 'sm-shop/target/surefire-reports/*.xml'
		    }
		}
    }
}