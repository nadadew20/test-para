pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'stg', 'prod'],
            description: 'Select the environment'
        )
    }

    stages {
        stage('Hello World') {
            steps {
                echo "Hello World! from trigger ${params.ENVIRONMENT}"
            }
        }

        stage('Hello Jenkins') {
            steps {
                echo "test the webhook from ${params.ENVIRONMENT} "
            }
        }
    }

    post {
           success {
        echo 'Pipeline completed successfully!!'
    }

    failure {
        emailext(
            to: 'nadahamdallah02@gmail.com',
            subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: """
Hello,

The Jenkins pipeline has failed.

Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Build URL: ${env.BUILD_URL}

Please check the console output for more details.

Regards,
Jenkins
"""
        )
    }
}
    }
