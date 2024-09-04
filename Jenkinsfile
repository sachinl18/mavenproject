pipeline {
    agent any 
    tools {
        maven "3.8.5"
    
    }
    stages {
        stage('Compile and Clean') { 
            steps {
                // Run Maven on a Unix agent.
              
                sh "mvn clean compile"
            }
        }
        stage('deploy') { 
            
            steps {
                sh "mvn package"
            }
        }
        stage('Build Docker image'){
          
            steps {
                echo "Hello Java Express"
                sh 'ls'
                sh 'docker build -t  sachinl:${BUILD_NUMBER} .'
            }
        }
        // stage('Docker Login'){
            
        //     steps {
        //          withCredentials([string(credentialsId: 'DockerId', variable: 'Dockerpwd')]) {
        //             sh "docker login -u sachinl -p ${Dockerpwd}"
        //         }
        //     }                
        // }
        // stage('Docker Push'){
        //     steps {
        //         sh 'docker push sachinl:${BUILD_NUMBER}'
        //     }
        // }
        stage('Docker deploy'){
            steps {
               
                sh 'docker run -itd -p  8081:8080 ashithss/assignment2:${BUILD_NUMBER}'
            }
        }
    }
}

