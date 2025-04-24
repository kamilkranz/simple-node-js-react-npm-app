// pipeline {
//     agent any
//     stages {
//         stage('Build') { 
//             steps {
//                 sh 'npm install' 
//             }
//         }
//     }
// }
pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                script {
                    docker.image("node:18.20").inside('-u 992:992'){
                        script {
                            sh"""
                            export HOME=.
                            npm install --prefix .
                            ls -la .npm
                            ls -la node_modules
                            """
                        }
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Workspace clean up'
            cleanWs()
        }
    }
}