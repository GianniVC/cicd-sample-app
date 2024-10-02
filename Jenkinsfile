node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker stop samplerunning'
            sh 'docker rm samplerunning'
        }
    }
    stage('Build') {
        build 'BuildSampleApp'
    }
    stage('Results') {
        build 'TestSampleApp'
    }
}

// pipeline {
//     agent any

//     // Automatically trigger the pipeline whenever a push is made to the main branch
//     triggers {
//         githubPush()
//     }

//     stages {
//         stage('Preparation') {
//             steps {
//                 // Stop and remove the existing running Docker container (if any)
//                 catchError(buildResult: 'SUCCESS') {
//                     sh 'docker stop samplerunning || true'
//                     sh 'docker rm samplerunning || true'
//                 }
//             }
//         }

//         stage('Build') {
//             steps {
//                 // Build the sample application by triggering a separate Jenkins job
//                 build job: 'BuildSampleApp'
//             }
//         }

//         stage('Test') {
//             steps {
//                 // Run tests by triggering a separate Jenkins job for testing
//                 build job: 'TestSampleApp'
//             }
//         }

//         stage('Deploy') {
//             steps {
//                 // Deploy the application using Docker (replace with your deployment logic)
//                 sh '''
//                     docker build -t sampleapp:latest .
//                     docker run -d --name samplerunning -p 80:80 sampleapp:latest
//                 '''
//             }
//         }
//     }

//     post {
//         success {
//             // Notify on success (optional: e.g., via Slack or email)
//             echo 'Deployment successful!'
//         }
//         failure {
//             // Handle failures (notify or take action on failure)
//             echo 'Deployment failed!'
//         }
//     }
// }
