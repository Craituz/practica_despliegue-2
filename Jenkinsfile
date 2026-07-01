pipeline {
    agent any

    tools {
        nodejs "Node25"
        dockerTool 'DockerTool'
    }

    stages {
        stage('Construir Imagen Docker') {
            steps {
                script {
                    docker.build('hola-mundo-node:latest', '.')
                }
            }
        }

        stage('Ejecutar Contenedor Node.js') {
            steps {
                script {
                    docker.image('hola-mundo-node:latest').run('-d --name hola-mundo-node -p 3000:3000')
                }
            }
        }
    }
}