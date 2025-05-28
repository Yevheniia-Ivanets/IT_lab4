pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Yevheniia-Ivanets/IT_lab4.git'
            }
        }

        stage('Build') {
            steps {
                bat '"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Debug'
            }
        }

        stage('Test') {
            steps {
                bat 'x64\\Debug\\test_repos.exe --gtest_output="xml:x64/Debug/test_report.xml"'
            }
        }
    }

    post {
        always {
            junit 'x64/Debug/test_report.xml'
        }
    }
}
