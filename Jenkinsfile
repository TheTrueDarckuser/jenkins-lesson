pipeline {
    agent any
    description 'Проект на С++ выводящий в консоль Hello World'
    stages {
        stage('Checkout') {
            steps {
                // Шаг для получения исходного кода из репозитория
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Шаг для компиляции исходного кода
                script {
                    def compiler = 'g++'
                    sh "${compiler} main.cpp -o main"
                }
            }
        }

        stage('Archive') {
            steps {
                // Шаг для создания артефакта (бинарного файла)
                archiveArtifacts 'main'
            }
        }
    }

    post {
        success {
            // Шаги, которые выполнятся при успешном завершении пайплайна
            echo 'Build successful. Artifacts are ready.'
        }
        failure {
            // Шаги, которые выполнятся при ошибке во время выполнения пайплайна
            echo 'Build failed. Please check the build logs for details.'
        }
    }
}
