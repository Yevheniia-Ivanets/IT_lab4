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
                // Збірка Visual Studio проєкту (Debug або Release)
                bat '"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Debug'
            }
        }

        stage('Test') {
            steps {
                // Запуск тестів з GoogleTest, збереження XML звіту
                bat 'x64\\Debug\\vs_mkr_test1.exe --gtest_output="xml:x64/Debug/test_report.xml"'
            }
        }
    }

    post {
        always {
            // Публікація результатів тестів у Jenkins через xUnit
            junit 'x64/Debug/test_report.xml'
        }
    }
}
