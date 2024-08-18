pipeline{

    agent any

// uncomment the following lines by removing /* and */ to enable
    tools{
       maven 'Maven 3.9.6' 
    }
    
    stages{
        stage('build'){
            steps{
                echo 'Compiling the App'
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                echo "Running Unit tests"
                sh 'mvn clean test'
            }
        }
        stage('package'){
            steps{
                echo "Packaging the app"
                sh 'mv package -DskipTests'
            }
        }
    }
    
    post{
        always{
            echo 'this maven pipeline has completed...'
        }   
    }
    
}
